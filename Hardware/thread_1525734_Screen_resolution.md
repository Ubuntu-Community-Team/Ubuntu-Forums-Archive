---
title: "Screen resolution"
date: 2010-07-07
forum: Hardware
---

### Post by groundhog136 on 2010-07-07
Monitor only displays in safe graphics mode - otherwise black screen.
Been digging around the forums and have got this far...

1. System>Preferences>Screen Resolution shows UNKNOWN and detects no displays
2. System>Administration>Hardware Drivers finds no proprietary drivers.

So, I can't enable any driver.

Where do I go from here?

---

### Post by dino99 on 2010-07-07
maybe you might need to talk a little about your hardware if you want effective help

try without xorg.conf:

sudo rm -f /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f

then reboot and check driver activation again

---

### Post by groundhog136 on 2010-07-07
Thanks dino99
 
I've just installed 10.04 and problem seems to be resolved (currently instaling updates but feeling confident)
 
Had been down the xorg.conf route but was feeling a bit out of my depth

---

