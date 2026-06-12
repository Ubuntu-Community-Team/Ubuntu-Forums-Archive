---
title: "error in configure file"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by calvinlyp on 2009-05-30
[FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]hi, 
 
i am using xubuntu 8.10.
i was installing a software called sharc from [http://sourceforge.net/projects/sharc](http://sourceforge.net/projects/sharc)  
 
after the command: 
 
./configure 
make 
 
it generate an error: 
cd . && autoconf 
/bin/bash: autoconf: command not found 
make: *** [configure] Error 127 

what i did is listed below and the error still appears:

1)apt-get update
2)apt-get install build-essential

i was told to like missing some [/COLOR][/FONT][/COLOR][/FONT][FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]developer support post-install.

may i know how about to install like [/COLOR][/FONT][/COLOR][/FONT][FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]make, imake, autoconf and (for many perl modules) gcc and a bunch of libraries and headers.

i read on the site [https://help.ubuntu.com/community/InstallingCompilers](https://help.ubuntu.com/community/InstallingCompilers)
about the paragraph on [/COLOR][/FONT][/COLOR][/FONT]
**[SIZE=2]Installing the GNU C compiler and GNU C++ compiler[/SIZE]**

it does not give much info on the command i should do to install.


pls help.
thanks.

---

### Post by calvinlyp on 2009-05-31
anyone can help?

i still not able install gmu development packages..:(

---

### Post by oldos2er on 2009-05-31
Have you installed autoconf? **sudo apt-get install autoconf**

---

### Post by calvinlyp on 2009-06-04
yes it works.

thanks alot.

---

