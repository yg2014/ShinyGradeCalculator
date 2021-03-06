---
title       : Grade Calculator
subtitle    : 
author      : YG14
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---
## Motivation
Provide students a tool to calculate the minimum required score that they need to get at the final test in order to get a certain letter grade
### Background:
- Many science instructors believe that students should  get a chance to improve their grade as the semester progress. This is particularly important in science classes because it is hard  and very often students get to understand the material only toward the end of the semester, only after they can see the whole picture. 
- One way to implement this philosophy is by dropping lowest interim test and count the final test twice (only in case that the final is higher)
- However, students have hard time to estimate how much they need to get in the final test in order to achieve a certain grade level, especially when multiple interim tests and other grade components are involved such as homework assignments. 
- This app is aimed at helping those students. 

--- .class #id 

## The Algorithm

#### Parameters
 - Test 1
 - Test 2
 - Test 3
 - Final Test
 - Homework
 - Final course grade
<br />each parameter account for 20% of the final grade

#### Math
   - Final course grade = Final Test + Homework + Test1 + Test2 + Test3
<br /> ... but if, for example test1 score is lower than the Final Test Score
   - Final course grade = 2 * Final Test + Homework + Test2 + Test3
   
Now, with a little algebra we extract the Final Test


---------------
## Examples
The function for calculating the desierd final test score is below: 

```r
finalTest <- function(t1, t2, t3, hw, grade) {
  #  case tf is not the lowest score 
  #  (i.e., tf is higher than the lowest test )
  tf <- grade *5 - (hw + t1 + t2 + t3)
  min <- min(c(t1,t2,t3))
             
  if ( tf >  min) {
    tf <- (grade * 5 - (t1 + t2 + t3 + hw) + min) / 2;
  }
  
  return(tf)
}
```

----
### now lets try:

```r
Test1 <- 70
Test2 <- 97
Test3 <- 89
Homework <- 95

# Desierd Final Grade 'A' (93)
grade <- 93

finalTest(Test1, Test2, Test3, Homework, grade)
```

```
## [1] 92
```

- You can find the Shiny app at: http://yg14.shinyapps.io/GradeCalculator

<center>Thank you for you time
## Enjoy!
</center>
