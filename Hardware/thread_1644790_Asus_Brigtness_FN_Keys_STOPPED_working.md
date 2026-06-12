---
title: "Asus Brigtness FN Keys STOPPED working"
date: 2010-12-13
forum: Hardware
---

### Post by maestrobwh1 on 2010-12-13
**[edit] the following is the result of a regression.  I keep seeing this term "regression" in ubuntu forums but not in the other distros.  It is frustrating.  Mainline ppa kernel 2.6.32-0206322712-generic installed.  Works with fglrx but had to dpkg-reconfigure a dkms package for my wireless rt8192se_pci (Realtek) to reinstall.  Everything seems to work fine.  Slightly slower boot.**

Running Lucid: The FN keys used to work, but recently, when pressed, the On Screen Display comes up, but no matter how much I tap the keys, the "slider" does not move on the OSD, nor does the brightness change; however, using the power management icon in the tray by manipulating the slider DOES work.


Any ideas why this stopped working or where to look for the cause?

This line exists in grub 
acpi_osi=Linux quiet acpi_backlight=vendor splash

and the VOLUME keys work fine so it is not a boot issue,

---

