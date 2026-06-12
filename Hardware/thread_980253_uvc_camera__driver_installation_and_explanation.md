---
title: "uvc camera / driver installation and explanation"
date: 2008-11-12
forum: Hardware
---

### Post by ^[H3ad-Tr1p]^ on 2008-11-12
hi buddies

I try to install  uvc driver for my logitech quickcam fusion

I have gone here [http://linux-uvc.berlios.de/#footnote-2](http://linux-uvc.berlios.de/#footnote-2)  and I was redirected here [http://linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial](http://linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial) for a new how to for compile a new module for cam

I wanted an explanation on this how-top because towards the bottom of the page there is some thing that I didn't understand

now,we can start from the beginner of the page,where it ask me to download the file...then if you see towards the bottom of the page,you can see that there is a detailed explanation for hardy that is my actual system [http://linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial#More_Errata](http://linuxtv.org/v4lwiki/index.php/How_to_build_from_Mercurial#More_Errata)

Note: On Ubuntu 8.04 (Hardy Heron)

now we can start to build module

apt-get install linux-headers-`uname -r` linux-source

with this command we have installed headers and source....but I remember that when I must compile some software,usual it is asked to me only headers... I seem   ..  can you explane this operation?

then more below ,it ask to me to link not headers but source  sudo ln -s /usr/src/linux-source-`uname -r` linux


then more below, it is very strange operations for me and I didn't understand

I had downloaded software like it was told at the beginning of the page,then I must to move on 

v4l-dvb

that is a directory that I have dowloaded

I didn't understand then,what I have to do... this command I didn't understand

rm v4l/.version

and I didn't get to carry out

I have then type make, and It had begun to compile many modules,so I have stopped the compilation because I don't know if I'll have compiled every modules built in the kernel ,and at this purpose I wanted some elucidation in what I'll go to do

at the final I didn't understand what is intended whit the last part of this how to,and what I have to find od when,whit the last command find like a report under 



and all should be good with the world. This was a supreme PITA, so I am hopeful that this will save somebody their sanity.

If you are having problems with a module not compiling, and it is not important to you, do a

find . -name my_bad_module_name.c -print

Then go to the directory that contains it. You will find a Makefile. Edit it and put a # at the start of the line that has the module name. 




thanks a lot and sorry for my bad english

---

### Post by ^[H3ad-Tr1p]^ on 2008-11-13
up :(

---

