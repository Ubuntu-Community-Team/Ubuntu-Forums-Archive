---
title: "Dell Inspiron 6400 - backlight stays on when the lid is closed"
date: 2008-11-04
forum: Hardware
---

### Post by Vzzzbx on 2008-11-04
Hi,

When I close the lid of my Dell Inspiron 6400 (with Intel 945GM video), the backlight randomly stays on.

This is a recurring problem in Gutsy, Hardy and now Intrepid (Feisty was fine, but I think it predates the current i810 driver).  Upon closing the lid, the backlight almost always flashes off and back on; sometimes it goes off again, but usually it just stays on.  I don't use suspend or hibernate.

Gutsy and Hardy were clean installations, so no wacky inherited settings were in play.  So far I've only tested Intrepid from the Live CD, but as the problem is identical and no launchpad bugs appear to have advanced in several months, I don't believe a complete installation would be any different.

I've done my own research (about a year of it) and tried every fix available, with neutral or negative results.  This thread is my last attempt to find a solution before I contribute to [bug 145809]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/145809").

The xserver-xorg-video-i810 package is installed, but so is the xserver-xorg-video-intel package.  [This page]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron6400") advises 'using' the i810 driver, but as Hardy's xorg.conf doesn't contain either 'i810' or 'Intel' I don't know what using the driver entails.

If you are aware of an absolute solution to this problem, please help me.

Many thanks,
Adam

---

### Post by Vzzzbx on 2008-12-08
Anyone at all?

---

### Post by Vzzzbx on 2008-12-22
sigh

---

### Post by Vzzzbx on 2009-01-23
Surely I'm not the only one for whom this is a problem.

---

### Post by Vzzzbx on 2009-02-18
If it worked in Feisty, it's something that can work again, right?  So the current driver is clearly broken, right?

---

### Post by JustinJS on 2009-02-19
I have the same problem on my E1405 any help?

---

### Post by Vzzzbx on 2009-04-24
It's still happening in Jaunty.

---

### Post by xodis on 2009-05-10
Comment out the 9th line (the one that says "if [ `CheckPolicy` == 0 ]; then exit; fi") of /etc/acpi/lid.sh. I hope that works!

---

### Post by Vzzzbx on 2009-06-04
Thanks for the reply! It does seem to have worked so far, but I'll keep it on watch for a couple of days and see if it keeps up.

---

### Post by Vzzzbx on 2009-07-10
It's absolutely working.  Thanks so much for the solution.

---

