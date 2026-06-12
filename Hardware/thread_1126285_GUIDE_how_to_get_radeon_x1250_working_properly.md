---
title: "*GUIDE* how to get radeon x1250 working properly"
date: 2009-04-15
forum: Hardware
---

### Post by jenova_skill on 2009-04-15
Well guys after playing with ubuntu now for a bit Installing / reinstalling /upgrading  with my laptop I've finally got the 100% sure fire way to install the GFX driver for my x1250 radeon card

Download the integrated motherboard driver from the ATI site x1250

Put it on your desktop and rename it something small I do ati.run

Uninstall all drivers proprietary and Open source drivers restart your computer this should boot you to ur CLI ( command line interface ) and fails to load up the GUI due to * no screens found *

From here you install your GFX driver 
 
cd Desktop
chmod a+x ati.run         
sudo ./ati.run

This will begin the install of the Ati driver after it's done You will be able to reboot and it will start ubuntu like normal.  HOPE THIS HELPS!!! It was the only thorn in my side getting to work most of the time.

---

