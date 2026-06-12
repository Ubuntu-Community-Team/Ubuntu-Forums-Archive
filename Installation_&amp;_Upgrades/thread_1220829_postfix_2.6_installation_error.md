---
title: "postfix 2.6 installation error"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by bilal_jan on 2009-07-23
hello everyone i am trying to install postfix on my ubuntu 9.04 from source
when i issue **make** command from terminal i am getting following error.
> 
make -f Makefile.in MAKELEVEL=Makefile
(echo "# Do not edit -- this file documents how Postfix was built for your machine."; /bin/sh makedefs) >makedefs.tmp  
No<db.h> include file found. 
Install the appropriate db*-devel package first.
See the Release_notes file for more information
make: ***[Makefiles] Error 1
make: *** [Makefiles] Error 2

i have read all Release_notes and i wasnt able to figure out the solution.
anyone here can tell me how to fix this up???

---

### Post by Partyboi2 on 2009-07-23
Hi have you got all the required packages installed?
You can install them from the terminal with
```
sudo apt-get build-dep postfix
```

---

### Post by bilal_jan on 2009-07-24
thanks **Partyboi2**... u really bring party to my life...it was million dollar worth of answer...thanks **buddy**

---

### Post by Partyboi2 on 2009-07-24
:lolflag:  You are welcome.

---

