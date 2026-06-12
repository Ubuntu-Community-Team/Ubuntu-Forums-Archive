---
title: "Live CD boot,  buffer I/O error on device sr0"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by devdeblib on 2009-01-10
I am receiving the following error when I try and boot into an 8.10 live cd: buffer I/O error on device sr0, logical block...etc

I have tried some things that have not helped so far, 

1. Ran memtest86
2. Configured the BIOS settings of my system to support UDMA2 instead of auto
3. Re-burned the disc @ 4x 
4. verified the md5 hash

Now I look at the BIOS and notice my one SATA controller has both my hdd and dvd, the dvd is on the slave channel. Would this make a difference when trying to boot the kernel?

---

### Post by ejprinz on 2009-02-01
I had a similar issue on several PC's and found that when I wrote the LiveCD iso image onto a DVD instead a CD, the Buffer I/O error went away. Also, the same iso image works on a USB Flash drive (but to create it I had to be able to boot into the LiveCD).

---

