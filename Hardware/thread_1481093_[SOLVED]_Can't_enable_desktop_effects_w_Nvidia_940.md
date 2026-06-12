---
title: "[SOLVED] Can't enable desktop effects w/ Nvidia 9400gt on Dell Dimension 2400"
date: 2010-05-12
forum: Hardware
---

### Post by corcoram on 2010-05-12
My system overview:
  Dell Dimension 2400 w/ Intel integrate graphics card
  Added Geforce 9400gt Card from Sparkle

Problem:
  Kept getting "Desktop effects cannot be enabled"

Solution:
After many hours, and the help of this forum, I was able to finally get desktop effects enabled on my Dell Dimension 2400 using a Geforce 9400gt card from sparkle.  Unfortunately, there is no bios setting for disabling the intel graphics integrated on the Dell Dim 2400.  Here are the notes I took to reproduce my Ubunto 10.04 install with Desktop Effects enabled:

1. Run Update Manager (if it doesn't run automatically)
   Reboot

2. System -> Administration -> Hardware Drivers
   Enable Current Version
   Reboot

3. From [http://ubuntuguide.org/wiki/ubuntu:lucid#compiz_fusion](http://ubuntuguide.org/wiki/ubuntu:lucid#compiz_fusion), run
   sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald librsvg2-common

4. Run "wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check"
   chmod +x compiz-check
   ./compiz-check
   NOTE: Will prompt to run sudo apt-get install mesa-utils
   re-run ./compiz-check shows "Warning: PCI ID 8086:2562 detected."

5. From [http://ubuntuforums.org/showthread.php?t=1467202](http://ubuntuforums.org/showthread.php?t=1467202), 
   sudo apt-get install ghex
   sudo ghex2 /usr/bin/compiz
   search for ASCII "8086:2562" and change it slightly - I changed the 2 to a 3.
   Reboot

6. System -> Preferences -> Appearance
   Select Extra and
   WALLAH - Extra effects are now running.

---

### Post by locon1980 on 2010-12-08
Great man!! you saved my life!!! working perfect!!!!!

---

