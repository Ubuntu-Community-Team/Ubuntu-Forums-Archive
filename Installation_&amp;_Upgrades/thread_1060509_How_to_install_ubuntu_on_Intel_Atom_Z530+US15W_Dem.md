---
title: "How to install ubuntu on Intel Atom Z530+US15W Demo board"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by davidking99 on 2009-02-04
Hi friends, recently, I got one Intel Atom Z530+US15W Demo board and I want to install ubuntu for test High Definition Video Decoder capability on linux environment. But I can't successful boot it up after install and fail at x-window start stage. Does anyone know how to do?

---

### Post by davidking99 on 2009-02-05
Where can I find the Intel Embedded Graphic Driver?

---

### Post by Galdor on 2009-02-22
> **davidking99 said:**
> Where can I find the Intel Embedded Graphic Driver?

Intel provides a driver package for Linux.
You can download it here:
[http://downloadcenter.intel.com/download.aspx?url=/13823/eng/IEGD-8.0-1.i386.rpm&DwnldId=13823&ProductID=2159&lang=eng](http://downloadcenter.intel.com/download.aspx?url=/13823/eng/IEGD-8.0-1.i386.rpm&DwnldId=13823&ProductID=2159&lang=eng)

Maybe this pages are helpful:
[http://support.intel.com/design/intarch/swsup/graphics_faq.htm?iid=ipp_rhc+graphics_faq](http://support.intel.com/design/intarch/swsup/graphics_faq.htm?iid=ipp_rhc+graphics_faq)
[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2159&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2159&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)
Unfortunately it is a RPM Package.
Eventually You can convert it with Alien.
KPackage can open and install RPM's.

Unfortunately KPackage finds missing dependencies.
:::::
rpm -U --replacepkgs --test  '///home/username/Path/IEGD-8.0-1.i386.rpm';echo RESULT=$?
error: Failed dependencies:
	/bin/sh is needed by IEGD-8.0-1.i386
	XFree86 is needed by IEGD-8.0-1.i386
RESULT=1

Sounds like this driver is made for XFree
Ubuntu uses X0rg.
For that I guess, one has to install XFree and remove X0rg before.
I treat that not to be recommended.

Does the standard VESA driver work?

---

### Post by jap1968 on 2009-03-20
> **davidking99 said:**
> Hi friends, recently, I got one Intel Atom Z530+US15W Demo board and...

Where did you get this board?

I could be interested in having one, too (If sold at an affordable price...)

---

### Post by runesvend on 2009-04-14
Hey davidking, take a look at this blog post with the very descriptive title "**Intel GMA 500 (Poulsbo) graphics on Linux: a precise and comprehensive summary as to why you’re screwed**":

[http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/](http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/)

It seems that the graphics driver will only work with a binary driver on Ubuntu 8.04 with a kernel version not newer than 2.6.24.

---

