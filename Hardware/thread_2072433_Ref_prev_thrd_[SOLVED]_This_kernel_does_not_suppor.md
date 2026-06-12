---
title: "Ref prev thrd: [SOLVED] This kernel does not support a non-PAE CPU"
date: 2012-10-17
forum: Hardware
---

### Post by spearz7 on 2012-10-17
lukeiamyourfather said: "Alternatively you could stick with 12.04 LTS until April of 2017."

The last two 12.04 updates that I received were pae.

Note the computer is 64-bit (only 2G memory), but I want to run 32-bit linux.

So am I stuck at 3.2.0-30?

If so, it that seems like a really big change for a LTS version with 4.5 yrs left to go. :(

---

### Post by oldfred on 2012-10-18
Welcome to the forums.

If your computer is 64bit it also is PAE. Only some older Intel chips were not PAE. So only if you have an old computer will the standard new PAE 32 bit version not work.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
> PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)
[http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

How To Install Ubuntu 12.04 On Non-PAE Capable Hardware.
[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more)
To see processor
lscpu
grep --color=always -i PAE /proc/cpuinfo


Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

### Post by spearz7 on 2012-10-18
Thanx for the welcome. Hope I don't wear it out :)

My bad for the poor description of the problem. I installed the 32-bit version of lubuntu 12.04 on a year old 64-bit computer using wubi. Kernel updates thru 3.2.0-30 were not pae, and all was good. Then, the last 2 kernel updates resulted in pae kernels, and the computer doesn't boot with either of them. The screen remains totally blank. As far as I know, I didn't "do anything" that would cause the updates to change to being pae.

The computer still operates normally when booted with the -30 kernel, so I would like to know if there is a way for me to get non pae kernel updates for kernels after -30. Otherwise I'll try to delete the pae kernels and then, pin -30. I saw a comment about compiling my own kernel, but that's more than I want to do right now.

---

### Post by oldfred on 2012-10-18
If computer is only a year or two old then PAE should not be the issue. It may be something that happened at the same time. 

But I do not know details of wubi as it just runs inside a file inside a NTFS partition and is not a full partitioned install.

---

### Post by spearz7 on 2012-10-19
I'm pretty sure you are right about it being something else. I removed all the pae files and installed the non pae versions. The computer still didn't boot, so my guess is that there was some change included in the -31 update that is causing the prob. That doesn't really explain why I started to get pae updates though.

I've pinned -30 and things are good again. Thanks for the feedback.

---

