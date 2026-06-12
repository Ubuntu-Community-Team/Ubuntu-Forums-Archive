---
title: "How to make a function in C"
date: 2008-10-08
forum: General Help
---

### Post by vandorjw on 2008-10-08
Hey,

I was wondering how I would make a function in C, so that it would  in the printf, I want it to evaluate myFunction at "x = 2" and "y = 3", and then print the answer. Then make on a new line, print the result of 1,1, etc.

This is what I am thinking so far, but it won't compile because there is something wrong with my syntax.

if there are any C programmers here, please help.

Thanks - CC7

PS: This is not the actual function, I just need an example. 



--------------------------------------------------------------------------
/*I have named this file, function.c*/

#include <stdio.h>
#include <math.h>

double myFunction( double x, double y){

double answer;

 if( x > 1){ 
 answer = x + y;
 return(0);}  // Do I need to return "answer" here?

 else if(x <= 1){
answer = x- y;
return(0);}

}

int main(){

printf("The answer to myFunction(2, 3) is %d \n;" myFunction(2,3));
printf("The answer to myFunction(1, 1) is %d \n;" myFunction(1,1));
printf("The answer to myFunction(2, 4) is %d \n;" myFunction(2,4));
printf("The answer to myFunction(0, 6) is %d \n;" myFunction(0,6));

return(0);
}
-------------------------------------------------------------------------


This is the error I get

fun.c: In function &#8216;main&#8217;:
fun.c:25: error: expected &#8216;)&#8217; before &#8216;myFunction&#8217;
fun.c:26: error: expected &#8216;)&#8217; before &#8216;myFunction&#8217;
fun.c:27: error: expected &#8216;)&#8217; before &#8216;myFunction&#8217;
fun.c:28: error: expected &#8216;)&#8217; before &#8216;myFunction&#8217;

---

### Post by -Zeus- on 2008-10-08
I think you should ask in a C forum.

---

### Post by niteshifter on 2008-10-08
Hi,

Missing the comma between args to the printf function:

```
printf("The answer to myFunction(2, 3) is %d \n;" myFunction(2,3));
printf("The answer to myFunction(2, 3) is %d \n;", myFunction(2,3));
                                                 ^
                                                 |
```

---

### Post by lma24 on 2010-11-08
> **cc7gir said:**
> Hey,
 
I was wondering how I would make a function in C, so that it would in the printf, I want it to evaluate myFunction at "x = 2" and "y = 3", and then print the answer. Then make on a new line, print the result of 1,1, etc.
 
This is what I am thinking so far, but it won't compile because there is something wrong with my syntax.
 
if there are any C programmers here, please help.
 
Thanks - CC7
 
PS: This is not the actual function, I just need an example. 
 
 
 
--------------------------------------------------------------------------
/*I have named this file, function.c*/
 
#include <stdio.h>
#include <math.h>
 
double myFunction( double x, double y){
 
double answer;
 
if( x > 1){ 
answer = x + y;
return(0);} // Do I need to return "answer" here?
 
else if(x <= 1){
answer = x- y;
return(0);}
 
}
 
int main(){
 
printf("The answer to myFunction(2, 3) is %d \n;" myFunction(2,3));
printf("The answer to myFunction(1, 1) is %d \n;" myFunction(1,1));
printf("The answer to myFunction(2, 4) is %d \n;" myFunction(2,4));
printf("The answer to myFunction(0, 6) is %d \n;" myFunction(0,6));
 
return(0);
}
-------------------------------------------------------------------------
 
 
This is the error I get
 
fun.c: In function ‘main’:
fun.c:25: error: expected ‘)’ before ‘myFunction’
fun.c:26: error: expected ‘)’ before ‘myFunction’
fun.c:27: error: expected ‘)’ before ‘myFunction’
fun.c:28: error: expected ‘)’ before ‘myFunction’
  you need only to add comma in printf:
printf("The answer to myFunction(0, 6) is %d \n" ,myFunction(0,6));
and leave space int main ( ) 
Hope it help:)

---

### Post by overdrank on 2010-11-08
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

