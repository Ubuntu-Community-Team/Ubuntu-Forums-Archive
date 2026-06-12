---
title: "Help needing in programing with C"
date: 2008-09-17
forum: General Help
---

### Post by vandorjw on 2008-09-17
Hi,
I have just started learning C and am trying to compile a program, a very basic calculator.

The code is attached, I make comments where I felt it was needed.
If you are somewhat experience with C, please help me out.

Thanks in Advance.

Cheers- CC7

This is the error I got when I tried to compile
> 
*****@*****:~/Documents/cProgramming$ **gcc improvedCalc.c -o tinyCalc**
improvedCalc.c: In function ‘main’:
improvedCalc.c:17: error: ‘div’ undeclared (first use in this function)
improvedCalc.c:17: error: (Each undeclared identifier is reported only once
improvedCalc.c:17: error: for each function it appears in.)
improvedCalc.c:19: error: ‘mul’ undeclared (first use in this function)
improvedCalc.c:21: error: ‘add’ undeclared (first use in this function)
improvedCalc.c:23: error: ‘sub’ undeclared (first use in this function)
improvedCalc.c:27: error: label ‘end’ used but not defined
improvedCalc.c:24: error: label ‘sub’ used but not defined
improvedCalc.c:22: error: label ‘add’ used but not defined
improvedCalc.c:20: error: label ‘mul’ used but not defined
improvedCalc.c:18: error: label ‘div’ used but not defined
improvedCalc.c: In function ‘add’:
improvedCalc.c:43: error: label ‘end’ used but not defined
improvedCalc.c: In function ‘sub’:
improvedCalc.c:58: error: label ‘end’ used but not defined
improvedCalc.c: In function ‘mul’:
improvedCalc.c:73: error: label ‘end’ used but not defined
improvedCalc.c: At top level:
improvedCalc.c:77: error: redefinition of ‘add’
improvedCalc.c:32: error: previous definition of ‘add’ was here
improvedCalc.c: In function ‘add’:
improvedCalc.c:85: error: ‘quote’ undeclared (first use in this function)
improvedCalc.c:88: error: label ‘end’ used but not defined
******@*********:~/Documents/cProgramming$ 


---

### Post by vandorjw on 2008-09-17
how do I delete double post?

---

### Post by nsche on 2008-09-17
Just a few things

1 - do not use goto.  This is c not fortran iv. use switch.
2 - You are reading one character (which is all you have storage for).
3 - you are using a bunch of undefined variables like mul and div.  Maybe you should be looking for 'm' and 'd' to compare to a single char.

You need to go back to the book.  I always liked K&R (1st ed).

YMMV
Norm

---

### Post by DGortze380 on 2008-09-17
> **nsche said:**
> Just a few things

1 - do not use goto.  This is c not fortran iv. use switch.
2 - You are reading one character (which is all you have storage for).
3 - you are using a bunch of undefined variables like mul and div.  Maybe you should be looking for 'm' and 'd' to compare to a single char.

You need to go back to the book.  I always liked K&R (1st ed).

YMMV
Norm

[www.cprogramming.net](www.cprogramming.net)

lots of tutorials that will give you all the syntax and logic you need for something like this.

---

### Post by vandorjw on 2008-09-18
Thanks for the help.

I do have a book called "How To Program C" by Deitel.

I just started reading it and trying some of the excersizes today.
When I came across the calculator one, I thought that it could be improved fairly easily, but then I found out its a little more difficult for me.

I am excited to learn C.
As soon as I have gone through the entire book, I think i'm going to learn O'caml.

Cheers - CC7

---

