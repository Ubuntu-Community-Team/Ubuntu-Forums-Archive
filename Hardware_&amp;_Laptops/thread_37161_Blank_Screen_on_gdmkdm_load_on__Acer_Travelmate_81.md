---
title: "Blank Screen on gdm/kdm load on  Acer Travelmate 8100"
date: 2005-05-26
forum: Hardware &amp; Laptops
---

### Post by Tetraptous on 2005-05-26
When I boot my laptop, upon loading gdm or kdm (or x.org in general for that matter), I get only a blank screen.  ctrl-alt-backspace cause the LCD to flicker, and ctrl-alt-f1 does get me a terminal.  I've tried dpkg-reconfigure xorg-xserver, I've reinstalled gdm and kdm, and I've looked through xorg.conf, but haven't found anything suspicious.  

The laptop has a Radeon Mobility X700 installed.

Has any one else gotten Kubuntu, or Ubuntu to work on this laptop?  What am I doing wrong?

Attached are the xorg.conf and Xorg.0.log files.

Thanks!

---

### Post by tread on 2005-05-26
A quick search of the forum (hint, hint :)) revealed [this](http://ubuntuforums.org/showthread.php?t=18701&page=1&pp=10). They start with a different laptop in the same series, but I think also discuss your particular model later.

---

### Post by Tetraptous on 2005-05-26
Thanks, I looked at that thread before, but somehow missed the part a few pages in where it explains what to do.  S0 now I have display up!

Now I have a garbled image, unfortunately.  A few others had that problem, but with my BIOS revision, they hadn't seemed to have found an answer.

---

