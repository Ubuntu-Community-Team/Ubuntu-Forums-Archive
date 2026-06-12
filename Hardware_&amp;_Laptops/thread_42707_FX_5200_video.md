---
title: "FX 5200 video"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by sue7504 on 2005-06-19
I've newly installed Ubuntu 5.04 but it hasn't automatically recognised my video card (I think a Geforce FX5200).  Currently my display will only run at 640x840.  In the past I know I've needed to edit an XF86 file but would appreciate some guidance.

TIA
Sue

---

### Post by Gezzer on 2005-06-19
try via a konsole

sudo dpkg-reconfigure xserver-xorg

u should be able to configure it from here ...

---

### Post by sue7504 on 2005-06-19
Thks Steve - worked a treat!

Sue

---

### Post by gnubie on 2005-06-19
Saw this thread today after installing ubuntu 5.04 on three different machines. Initially, ubuntu displayed at a high resolution but eventually settled on 640x480 after rebooting. Clicking on System/Preferences/Screen Resolution showed only 640x480 and I was stumped.

Thanks for this useful tip.

---

