---
title: "USB Scanner Canon LIDE 35"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by aclarion on 2006-10-26
I am a relatively new Linux user and tried Ubuntu off of the CD and it seemed really great, It almost made me switch from XP. However, my USB Scanner Canon LIDE35 does not work. How can I get it to work so I can finally switch?

---

### Post by magicfab on 2006-10-27
It is listed as supported at [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

From command line or synaptic, make sure you have sane-utils and xsane packages installed.

The genesys backend required is included since sane-utils 1.0.14.

If you are using Breezy or previous, i think you may have a too old version of sane-utils.

You can check with apt-cache show sane-utils.

---

