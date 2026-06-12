---
title: "Canon PIXMA MP540"
date: 2009-08-18
forum: Hardware
---

### Post by kaj on 2009-08-18
I have bought a Canon MP540, and I have the same problem as discribed here. I can't get the scanner to work.

I have downloaded and installed the factory drivers, and the printer works fine. But the scanner isn't recognized al all. In fact, the Canon MP540 is recognized as a usb-disk.

As recommended above, I have visited sane's website, and it seemes, that my scanner should work well with the same software, as other Canon MPxxx scanners. It is stated, that the backend version 0.16 should be used, but it is not possible to download anything newer than version 0.13 dated as far back as 2007.

Is there anything, I can do to get my scanner working?

Kaj Rasmussen
Denmark
kaj is online now Report Post   	Edit/Delete Message

---

### Post by stinger30au on 2009-08-18
unfortunaely thats the problem with these units that are all in one and suppoed to be the bees knees

u usually find the printer works but scanner doesnt

thanks the manufacturer for this & not helping out the linux programmers by giving them any info on how to make it work correctly

having said that, its only about 2 months till 9.10 comes out wait till then and try again

i learnt years ago after watching others struggle with these all in one units that they are more trouble then they are worth and i avoid them like the plague

---

### Post by Marg on 2009-09-04
I couldn't get the scanner to work with Sane and found it can 
use the Canon Scangear software instead.

For scanning I got it working as follows:
After extracting the printer driver downloaded from Canon 
there will be a MP540_debian_scangear.tar, which contains 
scangearmp-common_1.20-1_i386.deb (install this first)
scangearmp-mp540series_1.20-1_i386 deb (then install this)

now open a terminal and type scangearmp
this runs the Scangear software

---

### Post by bvpainter on 2009-10-22
I tried this but got message that "Cannot find Canon MFP scanner device".

Using Xsane I got message no scanner found.

---

