---
title: "Epson stylus photo 2100 driver problem"
date: 2014-11-02
forum: Hardware
---

### Post by amalgamas on 2014-11-02
I have had this printer for over 10 years and it has always worked well under ubuntu.

After upgrading from 12.04 to 14.04 I have problems with the paper feed.  When I start a job, the paper often is not fed into the printer and the red light lights up.  I press the paper feed button and the paper is drawn directly through the machine without printing and the led lights up again.  Sometimes the paper is drawn halfway into the printer and stops and the led lights up.  Other times it seemingly starts printing, but the paper does not move and I have to turn off the printer.

Before I buy a new printer, I decided to install the printer driver in a windows 7 laptop and try from there.  From windows 7 it works perfectly well!

Now I need advice.  I don't like to buy a new printer when the old one is not broken.  Obviously something has happened to the gutenprint driver between 12.04 and 14.04.  Is it possible to find and install the old driver?  Any other ideas out there?

---

### Post by amalgamas on 2014-11-11
Bump

It is very disturbing that a full working driver gets messed up during upgrades.  Can anyone give advice how to obtain and install the old driver?

---

### Post by Pilot6 on 2014-11-11
Here you can find the drivers

[http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult](http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult)

---

### Post by amalgamas on 2014-11-16
Yes, I have downloaded drivers from Epson (I think I have tried most things by now).  Problem is that there is no .deb and I get errors by ./config (which I was able to solve) and make.  This is the error:```
...
In file included from pfpng_ext.h:34:0,
                 from pfimg.c:39:
pfpng.h:33:17: fatal error: png.h: No such file or...
 #include <png.h>
                 ^
compilation terminated.
make[2]: *** [pfimg.o] Error 1
make[2]: Leaving directory `/home/bf/Downloads/Epson/sp2100/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bf/Downloads/Epson/sp2100'
make: *** [all-recursive-am] Error 2
```So there you are.  With my limited computing skills I am at an end with this wonderful printer.  For the first time in 5 years with linux I am now wondering whether to buy a mac

---

### Post by Mark Phelps on 2014-11-16
What might work is converting the .rpm file into a .deb file.  

Download the rpm file, it will be named something like> pips-sp2100_2200-cups-2.6.2-2.i386.rpm

Once you have that file, open a terminal, go to the directory containing the file, and enter the following:
> sudo alien --scripts pips*.rpm

When done, you will have a file in that directory with the same name, but ending in ".deb".

I don't have that Epson printer and can't test the deb, but when I opened it, it said that all dependencies were satisfied -- so it's likely to work.

Also, download the instructions file from the link -- it tells you what to do after installing the driver through CUPS.

---

### Post by bonzini on 2014-11-16
Have you tried the drivers in the repos?

I have an XP-610 which works fine with package printer-driver-escpr installed (this being v 1.4.1-1 in 14.10).

---

### Post by amalgamas on 2014-11-18
To Mark:
Good idea.  I tried it, but could not get it to work, even if i386 architecture is installed in my (amd64) system.  I gave the command (sudo alien --scripts pips*.rpm) and got this error message:> ... pips-sp2100_2200-cups-2.6.2-2.i386.rpm is for architecture i386 ; the package cannot be built on this system
.

To bonzini:
tried every driver I could find.  Nothing seems to work.  BUT: the driver is fine with windows 7, and always was fine before (ubuntu 12.04).  I am going to try my sons mac next.  That will be a cups driver, we'll see

---

### Post by Mark Phelps on 2014-11-18
>  installed in my (amd64) system.

Sorry, they only seem to have a 32-bit driver, not a 64-bit.

---

