---
title: "black screen after closing laptop lid and opening again"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by humbll on 2007-03-06
My Dell Inspiron E1505 has Ubuntu Edgy Eft installed. When I close the lid and return and open it, I have a black screen, the only way to get back in is to reboot. Any ideas how to fix this? I tried changing Power Management setting to DO NOTHING when lid is closed but it had no effect.

---

### Post by dashnak on 2007-03-06
As far as I know, neither hibernate nor suspend work on that laptop, I'm still searching for a fix myself, it's pretty annoying if you ask me...

---

### Post by wonderfullyrich on 2007-05-23
I'm experiencing a similar problem on a Dell Latitude D420 running Fiesty.  The suspend & hibernate fuctions work fine on this laptop (minus an intermittent problem with ipw3945 drivers).  I've set the power management to "do nothing" on a laptop lid close, but it doesn't seem to help.  Anyone else find a fix to this?

---

### Post by mjitkop on 2007-05-23
I have the same problem with one Inspiron E1505 too but it's with Windows XP! I think it could be a hardware problem rather than a problem with Ubuntu. ;)

---

### Post by jhd002 on 2007-06-02
I think I have also seen this occasionally on my Inspiron E1505 under XP. My resolution has always been to use the <Fn> <F8> key combination to cycle through the CRT/LCD options until the screen comes back.

---

### Post by holotone on 2007-06-16
Exact same problem here on my brand spankin' new E1505 with Feisty installed by Dell. Any solutions out there yet?

---

### Post by psicus78 on 2007-06-18
me too...with a new E1505 with Feisty from Dell...bad stuff! :(

---

### Post by psicus78 on 2007-06-18
if someone wants to try this:

[http://www.reactivated.net/weblog/archives/2007/05/dell-laptop-lcds-not-powering-up-on-lid-open-event/](http://www.reactivated.net/weblog/archives/2007/05/dell-laptop-lcds-not-powering-up-on-lid-open-event/)

I'll wait... :)

---

### Post by holotone on 2007-06-19
I've found a fix that seems to have worked perfectly for me, via the helpful folks at Freenode's #ubuntu:

```
sudo apt-get install  xserver-xorg-video-intel
```

This installs a newer video driver for the Intel 945/950 card that the e1505 has. Not only does this resolve the lid problem, but also numerous Beryl related oddities as well.

---

### Post by GoodPanos on 2007-09-25
> I've found a fix that seems to have worked perfectly for me, via the helpful folks at Freenode's #ubuntu:
I just wanted to concur this solution also worked on my Dell Latitude D420.  :) It also fixes some other issues with external monitors.

---

