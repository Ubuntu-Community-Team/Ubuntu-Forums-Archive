---
title: "how to install gnu development packages?"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by calvinlyp on 2009-05-31
hi all,

i am relatively new to linux platform.

i am using xubuntu 8.10 and also ubuntu 8.10

i recently installed a software while using the platform of ubuntu 8.10
the software requires some gcc and g++ compiler thus i use the command below to install:

[FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]1)apt-get update
2)apt-get install build-essential

after which i am able to install perfectly fine.

next i try using another platform xubuntu 8.10 onto another desktop.

this time it show some error, 
[/COLOR][/FONT][/COLOR][/FONT][FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]
after the command of installing the software: 
 
./configure 
make 
 
it generate an error: 
cd . && autoconf 
/bin/bash: autoconf: command not found 
make: *** [configure] Error 127 [/COLOR][/FONT][/COLOR][/FONT]
[FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]
[/COLOR][/FONT][/COLOR][/FONT][FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]i was told to like missing some [/COLOR][/FONT][/COLOR][/FONT][FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]developer support post-install.

may i know how about to install like [/COLOR][/FONT][/COLOR][/FONT][FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]make, imake, autoconf and (for many perl modules) gcc and a bunch of libraries and headers.

i read on the site [https://help.ubuntu.com/community/InstallingCompilers](https://help.ubuntu.com/community/InstallingCompilers)
about the paragraph on [/COLOR][/FONT][/COLOR][/FONT]
**[SIZE=2]Installing the GNU C compiler and GNU C++ compiler[/SIZE]**

it does not give much info on the command i should do to install.


pls help.
thanks.

---

