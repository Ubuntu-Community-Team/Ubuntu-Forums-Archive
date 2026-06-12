---
title: "How to enable UDF support to Hoary and use it to format DVD+RW with UDF filesystem"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by jery_wang2002 on 2005-03-30
Hi,

I am not an expert in Linux. I'd like to know how to add UDF support in Hoary.

I have tried it by googling around. And so far I can have a DVD+RW formatted in UDF and write some files on it. But my configuration is not reliable and have so many problems:

1. Cannot eject.
2. Cannot autodetect from Nautilus etc.

What I have done so far:
1. install udftools
2. Modify /etc/default/udftools to match my system
3. Added /dev/pktcdvd/dvdwriter /media/dvdrw   udf    ..... (I cannot remember exatcly as I am not in front of my Linux/Hoary desktop now)
4. I manage to format CDRW using cdrtool -d /dev/hdd -q. But strangely, this doesn't work for DVD+RW. I had to use mkudffs ...... But when I try to copy large directories, it stopped halfway.



If someone had done this and share it with us, would be wonderful. 


Many thanks.
Jerry

---

### Post by Levander on 2005-07-29
I was trying the same thing for the last couple of days, and think I've just given up. I'm really starting to think the udftools package in universe just doesn't work.  Really I'm surprised you got anything to write onto your DVD-RAM at all with this package.  

One of the things that makes me think this package does not work anymore is that if you looks at the udftools cvs repository at [http://cvs.sourceforge.net/viewcvs.py/linux-udf/](http://cvs.sourceforge.net/viewcvs.py/linux-udf/), it looks like the most recently modified file was 17 months ago.

Unfortunately, I think tonight I'm just going to write a script that creates an iso to backup my system.

Here are the links to stuff I've posted about this issue:

[http://ubuntuforums.org/showthread.php?t=52464](http://ubuntuforums.org/showthread.php?t=52464)
[https://launchpad.ubuntu.com/malone/bugs/1615](https://launchpad.ubuntu.com/malone/bugs/1615)

Apparently launchpad is where you report bugs in universe for ubuntu.

---

