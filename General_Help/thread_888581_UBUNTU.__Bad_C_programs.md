---
title: "UBUNTU.  Bad C programs?"
date: 2008-08-13
forum: General Help
---

### Post by Len Tyree on 2008-08-13
UBUNTU:   C programs.  I moved many C programs to Ubuntu from Windows xp.  Now, I can not get any of them to run??  They were created on windows 98se running under DOS.  Do i need to recompile them in Ubuntu?  To my way of thinking, they should run where they are.
A little help, please?  Thank you, Len Tyree.

---

### Post by dexter.deepak on 2008-08-13
as you know C is not a platform independent language, so you have to recompile the code on ubuntu.
install build-essential package:
```
sudo apt-get install build-essential
```
for beginners, i think geany is a good alternative to turbo-c on windows
```
sudo apt-get install geany
```

now run your code, and report your errors here...only then can we help you.

---

### Post by Len Tyree on 2008-09-01
Got gean, thanks to dexter.
Looks like quite a powerful tool,  Now just need to know how to work it!!!  No problem.  thanks again, len.

---

### Post by Len Tyree on 2008-09-29
problem SOLVED, thanks to all.

---

### Post by DrMega on 2008-09-29
> **dexter.deepak said:**
> as you know C is not a platform independent language, so you have to recompile the code on ubuntu.

Actually the C standard as defined by ANSI *is* a platform independant language. It is the various platform specific extensions that break it.

Of course only the language has been standardised. The compiled executable is platform specific.

---

### Post by nsche on 2008-09-29
Wine is a program for running windows programs on Linux.  Just install it and use it to run your .exe files.

---

