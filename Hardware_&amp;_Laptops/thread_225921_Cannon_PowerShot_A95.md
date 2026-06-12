---
title: "Cannon PowerShot A95"
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by bozemblem on 2006-07-30
Hello everyone.  I'm trying to connect my Cannon PowerShot A95 camera to my computer and I'm having some difficulies.  I'm trying to install Capture (version 1.0.3cvs20060706) which has as a dependency libptp2 (version 1.1.0).  When I try to compile libptp, I get the following error:

...
make[2]: *** [ptp.lo] Error 1
make[2]: Leaving directory `/home/mjhenry/Desktop/libptp2-1.1.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mjhenry/Desktop/libptp2-1.1.0'
make: *** [all] Error 2


First of all, is there an apt package for Capture, or another software package that has the same functionality.  If not, has anyone had any luck getting this to work and how did you do it?  Thanks!!

---

### Post by gogolok on 2006-08-06
You need to paste a few lines above.

But I guess you will need the following patch for gcc4:
[http://svn.exactcode.de/t2/trunk/package/graphic/libptp/gcc4.patch](http://svn.exactcode.de/t2/trunk/package/graphic/libptp/gcc4.patch)

---

### Post by brak2718 on 2007-04-11
Indeed, something weird with gcc 4.0.

On Ubuntu 6.06, this worked for me:

env CC=gcc-3.3 ./configure
env CC=gcc-3.3 make

--Ryan

---

