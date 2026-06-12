---
title: "Error while installing lexmark z65"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by hans030390 on 2006-08-23
Lexmark has linux drivers for my Z65 printer, so I tried installing them.

I used the method found in the other How to for lexmark printers, and when I get to the alien part, I get some error:

root@ubuntu:/home/me/Desktop/CJLZ65LE-CUPS-1.0-1/installer# alien -i z65llpddk_2.0-3_i386.deb
Warning: Skipping conversion of scripts in package z65llpddk: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
dpkg: error processing z65llpddk_2.0-3_i386.deb (--install):
 trying to overwrite `/usr/include/lexmark/alignmentdata.h', which is also in package z600llpddk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 z65llpddk_2.0-3_i386.deb

for the other file, with the cup title, it works fine...but, I still went ahead and tried to install it and it didnt work...I think this stops me.

There was also an error before that, but I was told to ingore it:

root@ubuntu:/home/me/Desktop/CJLZ65LE-CUPS-1.0-1# sh lexmarkz65-CUPS-1.0-1.gz.sh -keep
Creating directory installer
Verifying archive integrity...OK
Uncompressing Lexmark Printer Driver............
ls: /usr/lib/libtcl?.?.so: No such file or directory
ls: /usr/lib/libtk?.?.so: No such file or directory
./install: line 15: ./xlexinstall: No such file or directory
The program returned an error code (127)

I installed the z600 drivers for my z705 printer, but it only does black and white. I really want to get my z65 working, because others have done it on Ubuntu before...so I don't know why mine wont work, especially if installing the z600 ones were fine.

Help!

---

