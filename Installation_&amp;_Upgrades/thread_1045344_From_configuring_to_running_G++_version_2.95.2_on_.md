---
title: "From configuring to running G++ version 2.95.2 on Ubuntu 8.04."
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by ahiggin5 on 2009-01-20
Hello everyone.  First, let me give you some background information about myself and my current situation.  I need to use "Supermix," which is a c++ library for a research project I am working on.  For other reasons, I require the use of Ubuntu to run other scientific programs.  

I was not the person who configured the computer system and I do not know the first thing about running ANYTHING from a terminal.  I come here seeking help in getting Supermix operational.

I've done some preliminary work on this issue:  the website elucidating Supermix can be found here:  [http://www.submm.caltech.edu/supermix/](http://www.submm.caltech.edu/supermix/).  I notice that Ubuntu is not on their list of "system requirements."  

My first question is can Ubuntu be used to run any of the prescribed g++ versions listed there (e.g. 2.95.2)?  In preparation for a "Yes! Ubuntu can compile and run Supermix if you have the correct version of g++," I have downloaded all the versions listed there.  

I do not know the first thing about configuring/building/testing/running a program which doesn't automatically do these things when i click on a .exe file (like in windows).  If anyone could please take the time to give me step-by-step instructions on how to do these things so that I can begin playing with Supermix, considering I don't know the jargon of linux, I would be MOST appreciative.


Thanks for your time,
Andrew

---

### Post by ahiggin5 on 2009-01-22
Bump.  I haven't stumped you guys, have I?

---

### Post by taurus on 2009-01-22
How old is that page anyway, talking about RedHat 6 & 7?  And besides, the link to download the source, supermix.tar.gz, is wrong--dead link.  It should be here.

[ftp://ftp.submm.caltech.edu/pub/supermix/](ftp://ftp.submm.caltech.edu/pub/supermix/)

Looks like it is compiling just fine on intrepid running gcc version 4.3.2.  Don't forget to install the build-essential package first.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

