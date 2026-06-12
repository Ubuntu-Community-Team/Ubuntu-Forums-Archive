---
title: "Kernel Compilation with gcc-4.4"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by UnseenMenace on 2006-01-05
Although I am a Linux newbie i have recently compiled my first ever kernel for ubuntu with the source 2.6.12 however this was done using gcc-3.4 using the excellent guide found [here on the ubuntu forums]("http://www.ubuntuforums.org/showthread.php?t=56835&highlight=kernel+compiling")

Now however I need to compile the kernel using gcc-4.4 - having installed this and removed gcc-3.4 following the guide as I had previously obtains the following error

> /usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] Error 127
make: *** [scripts_basic] Error 2

Now im not surprised that it can not find gcc-3.4 as I removed it in the hope that the kernel would then compile using gcc-4.4 however this is not the case

Would someone please be so kind as to tell me how to resolve this situation if its possible

---

### Post by charlieg on 2006-01-06
There is no such thing as GCC 4.4 at the moment of writing.  Latest (stable) release is 4.0.2 according to [gcc.gnu.org](gcc.gnu.org).  Do you mean 3.4?

---

### Post by UnseenMenace on 2006-01-07
Opps thats the newbie in me coming out  :rolleyes:  - No helping some people

I actually have gcc 4.0.1-4

Now that my stupidy has been corrected can you help me regarding this issue ?

---

### Post by cborge on 2006-01-08
I get the exact same error. command not found. I have gcc version 4.0.2, and I need the 3.4 version to be able to compile some programs.
The problem is I don't know how to do that. I have tried "apt-get install gcc-3.4" but that does not work.

Anybody?????

---

