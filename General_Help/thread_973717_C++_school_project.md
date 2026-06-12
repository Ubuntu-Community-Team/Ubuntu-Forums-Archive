---
title: "C++ school project"
date: 2008-11-06
forum: General Help
---

### Post by packman86 on 2008-11-06
Hey,

I have trouble with a programming assignment.

We are supposed to create a function (reverse_array int a[]) to change the order of the numbers that are put into the program

for example:

1 2 3 4 5 6 7 8 9 0
=
0 9 8 7 6 5 4 3 2 1

Anyone that can help me?

---

### Post by geoffjay on 2008-11-07
for(i=0,j=9; i<10; i++)
  tmp[j--]=a[i];

I don't think these forums are really the right place to have someone do your homework for you but the geek in me couldn't resist answering the question.

Go to [http://www.cplusplus.com/](http://www.cplusplus.com/) instead.

---

### Post by tiberiup on 2008-11-07
Or if  a[]=1 2 3 4 5 6 7 8 9 0 is a number(the function has a bug, if the last digit of the number is 0 the reverse number cannot begin with 0), hope that is correct i forgot the C++ sintax :)  :

reverse_array (int a[])
{
 int reverse,nr;
 reverse=0;
 nr=a[];
 while(nr)
   {
 reverse=reverse*10+(nr%10);
 nr=nr/10;
   }
 return reverse;
 }

---

### Post by packman86 on 2008-11-07
thanks a lot guys :)

Close thread!

---

