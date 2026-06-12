---
title: "V25 Graphics"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by matt91 on 2007-12-01
I have a Samsung V25 laptop which i have installed ubuntu on (alternate install). I am trying to get the display to work but so far have not managed to do this. All i know is that it can do 1024x768@60Hz and uses Intel 82845G graphics. i have tried editing the xorg.conf with a modeline generated with [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) and this does not do anything.

When my ubuntu starts up, it goes through the boot screen as normal and then goes to reminal text with the last line being something like "running local boot scripts [OK]" and then to a blank screen.:confused:

thanks to anybody that can help, Matt.

---

### Post by matt91 on 2007-12-02
*Bump*

---

### Post by RiazM on 2008-04-07
I have the same problem. I can drop into one of the terminal things with alt ctrl f2, so I think this problem should be fixable, though I don't really know how. 

I have tried running 

sudo dpkg-reconfigure -phigh xserver-xorg

but this has not helped. 

The display used to work on xubuntu 6.10. If only i had kept the xorg.conf.

---

### Post by RiazM on 2008-04-07
hey ho, i just installed the gutsy beta and everything works fine by default now. Hurray.

---

