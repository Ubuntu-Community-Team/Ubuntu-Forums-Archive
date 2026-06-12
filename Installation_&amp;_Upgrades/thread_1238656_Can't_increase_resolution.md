---
title: "Can't increase resolution"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by wurlyfan on 2009-08-12
[SIZE=2]Hi ... I just installed standard Ubuntu Jaunty 9.04 on an ASUS M6A laptop (1.8 GHz Centrino, 2 GB RAM) and can't get the screen resolution above 800x600. The machine uses the Intel 915GM/GMS Express Chipset, which seems to be recognised by the installer, but I had errors during the installation (no usable screen modes). Reading other posts I seem to have resolved these errors and Ubuntu now [/SIZE][SIZE=2]starts normally[/SIZE][SIZE=2], but with limited resolution modes.

I'm using Ubuntu on my desktop, but I'm still a relative noobie, can anyone please help?[/SIZE]

---

### Post by pizza-is-good on 2009-08-12
A good place to start will be checking drivers.
 
Go to 
System >> Administration >> Hardware Drivers
and make sure that you are using your graphics card's recommended driver.
 
Post to let us know if that fixes it.
 
Good luck, and welcome to Ubuntu.

---

### Post by wurlyfan on 2009-08-12
Thanks for reply. The Hardware Drivers screen says "No proprietary drivers are in use ...". Not good, huh? I have downloaded a driver from Intel (i915Graphics.tar.gz) but I don't know how to install it (or even if I should)! There sems to be no Linux suppport from ASUS.

---

### Post by pizza-is-good on 2009-08-12
In 'hardware drives' you should look for one that says something like 'non-free'. Click on it and then activate.
 
I'm not sure how to install a driver from a file, and not sure if it would even work.

---

### Post by wurlyfan on 2009-08-12
Yeah, the Hardware Drivers screen is empty, so no go there. Thanks for the suggestion, though

---

