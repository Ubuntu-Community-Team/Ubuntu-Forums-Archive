---
title: "gateway c 141 x"
date: 2009-02-10
forum: Hardware
---

### Post by gothmog1114 on 2009-02-10
Is there any way to get the tablet functions on ubuntu? I'm on a gateway c 141 x, running Ibex.

Ive also tried running vista on a virtual machine, but i cant get it to recognise my pen input either. any help would be greatly appreciated****.

---

### Post by Favux on 2009-02-10
Hi gothmog1114,

It shouldn't be too hard.  Given that it has a built in Wacom tablet.  The only question is is a serial or usb Wacom tablet?  Try:
```
dmesg | grep [Ww]acom
```
in a terminal.  Hopefully the output will tell us if you don't already know.  And also:
```
dmesg | grep ttyS
```

First go here:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

Do not do the HOW TO part on compiling (section 1)!  Instead use the link to Loic2's Wacom wiki, near the top, and get the two i386 debs (you have Intel duo cores, correct?).  Just down load and dbl-click to install them.

Then we need to configure your xorg.conf.  Section 2 of the HOW TO.  For that we need your xorg.conf (in /etc/X11).  And we need to know what Wacom features your tablet has.  Stylus, eraser, side-switch (buttons on stylus; 1 or 2, etc.), touch?  Attach a copy of your xorg.conf to your next post.  And also the output of the two terminal commands.

Then after we get your stylus working we need to calibrate it.  Section 3 of the HOW TO.

---

