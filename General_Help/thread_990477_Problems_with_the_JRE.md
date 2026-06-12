---
title: "Problems with the JRE"
date: 2008-11-22
forum: General Help
---

### Post by mttman on 2008-11-22
Hello,

I am running a new install of 8.10, I did a full format reinstall when 8.10 came out and I am having a problem with programming in java. Java appears to be version 1.6.0_10 but whenever I try to use the scanner class I get an error indicating that it can't be found, it's almost as if java is version 1.4 or lower. 

```
$java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)

```
```
java <program using scanner>
Exception in thread "main" java.lang.Error: Unresolved compilation problem: 
	scanner cannot be resolved

	at StdIn.readString(StdIn.java:24)
	at EditDistance.main(EditDistance.java:35)

```
I know that this is a problem with java or some aspect of the installation because my code has compiled and run in a linux lab on my campus (I believe they run Fedora 7).

Any help you can give me would be great

Thanks in advance
<Mttman>

---

### Post by reality1011 on 2008-11-22
post your code

---

### Post by mttman on 2008-11-25
I found the problem, there was a bug in my code. but I still don't understand why it would compile on another machine with the bug still there.

if there is someone out there that could answer this for me I would appreciate it. 

Thank you

---

### Post by TeXtonyx on 2008-11-25
Back in the days when I was designing webpages, I had to check my
html in both Internet Explorer and I think it was (Mac) Netscape. The
same code would work in one browser and not the other. Usually it
was bad code that broke one webpage and worked in the other because
one would have a slacker standard or poorly written code itself.

I think you should also check your java code on a Windows machine
because you will increase your chances of finding errors in your code. 
You can expect different results and it will nearly always be due to 
errors in your code due to lax and strict interpretation of your code.
Remember the people who created java are also human, and to err is ...

---

### Post by mttman on 2008-11-26
thanks, i think i understand better

---

