---
title: "Vaio R505GL jogdial won't stop scrolling"
date: 2008-07-29
forum: Hardware
---

### Post by jippers on 2008-07-29
Hello,

I have an aging Sony Vaio R505GL laptop.  I believe it's scroll wheel is supported in linux by the module sonypi, but I may be wrong.

The problem with 8.04 I'm having is once I use the scroll wheel on the laptop, the screen I'm currently in won't stop scrolling.  It seems to be buffering multiple "scroll wheel" events because eventually my ctrl+backspace to kill X is read by the computer and X is shutdown.  

Any ideas as to what's wrong or how I can fix it?

---

### Post by RtVD on 2008-10-04
Having identical issue with a Sony Vaio PCG-R505DL.

this guy ended up just gluing his scroll-wheel:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/230391]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/230391")

---

### Post by scallopedllama on 2008-11-14
see here:
[http://ubuntuforums.org/showthread.php?p=6180651#post6180651](http://ubuntuforums.org/showthread.php?p=6180651#post6180651)

I got this working with gutsy gibbon, but Intrepid ibex is still fighting me

---

