---
title: "NDISwrapper for windows drivers"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by Simulachra on 2007-10-23
In my Cognitive Science lab I'd like to run Xubuntu on the computer that has an A/D converter hooked up to it via USB (an iWorx 214) for physiological testing.  The only software I know that can interface with the iWorx unit is the software provided by the same company that manufactures the unit--LabScribe2.

Though there is no linux driver nor has LabScribe2 been ported to linux, I figured I could run LabScribe2 in WINE.  I completely forgot about the driver though.

I googled a bit and found that NDISwrapper could be used to make a windows driver work.  I haven't tried anything yet other than install xubuntu on the machine because I thought I'd ask first if what I'd like to do is possible.  If not, i'll have to go back to XP on that machine which I REALLY would rather not do.

I checked other threads that I thought may pertain to this issue but they were concerned with wireless drivers, and I think my situation is different.  Thank you.

---

### Post by Ltselan on 2007-10-23
NDISwrapper is specifically for wireless drivers, and to my knowledge will only work for wireless drivers. The NDISwrapper project goal is to incorporate the NDIS (Network Driver Interface Specification) API into the windows kernal and then interface with windows drivers. There are more details at [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

Also, if NDISwrapper could work with other drivers, then printer and scanner compatibility with Ubuntu would not be such a problem. And since since there is huge compatibility issue, I don't believe such an approach will work for you.

Hopefully a more experienced member can provide you with suggestions for an alternative. My guess though is that you will need to either write the drivers yourself, find someone to do it for you, or find a way to write a program that functions similar to NDISwrapper for your particular application.

---

