---
title: "Ibm T43 Display Help"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by FunnyLookinHat on 2005-08-31
This will probably help those with any of the Intel 900 graphics displays... but I specifically have an IBM T43 1871.  It uses the new Intel 900 graphics, which suck.

Basically, I was getting a black screen when ubuntu would boot up but I knew that it was a display issue because I was receiving VBIOS errors and whatnot.  I tried doing several things but finally got it to work by running xorgconfig, and setting it to use VESA.  I then went back into the config file and made sure that it was really using VESA and not whatever it defaulted to.

I'm attaching my xorg.conf, it should work as is, but make sure you back up your current xorg.conf if you have anything working as it is.  Just change the name from xorg.conf.txt to xorg.conf and place it in your /etc/X11/ directory.

---

