---
title: "Barely Readable Desktop - Display Problem"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by dsirkka on 2007-08-21
Hello All,
I am new to Ubuntu and have just installed it on a Japanese Fujitsu Desktop. My problem is that the display is totally messed up.  The colours are totally off and I can barely make things out.  I have searched for a solution but to no avail.  My manual does not give the optimum refresh rate but I assume it is 60.  I have a 17 inch widescreen TFT monitor with a resolution of 1280x768 capable of 24bit display.  I have run the automatic configuration tool again... that didn't work and I have even played around with xorg.conf but to no avail.  My resolution is set properly.
Any ideas?
Thanks,
Doug

---

### Post by dsirkka on 2007-08-21
I should probably add here that when I boot from CD I get the same problem but not when I start in safe graphics mode.  THen everything is fine.

---

### Post by dsirkka on 2007-08-21
Any chance somebody can help?

---

### Post by dsirkka on 2007-08-22
Well, I'm going to answer my own question here.  It only took me about 20 hours to figure it out.   Thanks for all the help.

Since Ubuntu displayed fine when booted from the CD in safe graphics mode (using the VESA driver) I simply copied the xorg.conf from the CD setup and replaced it on my harddrive in /etc/X11.
In other words I changed the SiS 650 driver with VESA (I think), even though it should have been the right driver.

Doug

---

