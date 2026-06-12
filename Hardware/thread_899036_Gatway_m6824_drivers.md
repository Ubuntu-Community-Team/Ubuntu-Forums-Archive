---
title: "Gatway m6824 drivers"
date: 2008-08-23
forum: Hardware
---

### Post by frenchsquared on 2008-08-23
something happend
Earlier today my computer was running Ubuntu just fine
I updated to the newest version yesterday and for the first time ever the computer had sound. I was paling around with wine and suddenly my wifi card isnt working and the sound is gone. I have no idea how to track what happened or how to reinstall the drivers. Something also seems wrong with the graphics driver. Has an onboard ATI card

---

### Post by frenchsquared on 2008-08-23
here are the specs
#
Processor: Intel Core 2 Duo CPU T5250 @ 1.50GHz, 2MB L2 Cache, 667MHz FSB
#
Display: 15.4” widescreen Ultrabright (glossy) WXGA TFT (1280x800)
#
Memory: 3GB DDR2 667MHz (upgradable to 4GB)
#
Video: ATI Mobility Radeon HD 2400 XT Dedicated Graphics with up to 892MB Hypermemory (128MB GDDR3 dedicated)
#
Hard Drive: 250GB 5400RPM SATA

---

### Post by frenchsquared on 2008-08-23
gordon@Gateway:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c8

gordon@Gateway:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:94c8 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found

---

