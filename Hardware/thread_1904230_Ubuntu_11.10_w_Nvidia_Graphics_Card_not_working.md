---
title: "Ubuntu 11.10 w Nvidia Graphics Card not working"
date: 2012-01-04
forum: Hardware
---

### Post by Sverige_Torsten on 2012-01-04
Watch this video I just created (and is uploading): [http://youtu.be/vVgV2J_mHTQ](http://youtu.be/vVgV2J_mHTQ)

My system:
Hardware: Fujitsu NH751
Software: Ubuntu 11.10 alternate cd, full disc encryption.

To put it quick:
1. Do a fresh install of Ubuntu 11.10 with Alternate CD, X64-bit (**probably** any dist of 11.10 will work).
2. Use another computer to download and burn **SuperGrub2** iso.-image to a cd/dvd and **boot with it** (or create a bootable usb-stick with it).
3. Select the Third option: "Detect Grub .cfg" and boot with it (press Enter two times).
4. Wait 10 seconds and enter your full disc encryption key and press Enter, **even if the screen still is black**.
5. Wait 30 seconds and you'll have the 11.10 login menu with perfect drivers and hardware acceleration.
6. Use Software Center to install GNOME Shell.
7. ENJOY!

:p

The installation is not really "fresh" since i installed all the updates and some additional software. That does not concern the solution to the "Nvidia bug" anyhow, since I applied it before downloading updates and GNOME Shell (yes, you too could do it safely). :D

Here is a link to supergrub2, used in the video: [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

And by the way, I have not installed the "additional drivers" available since I think those could mess up the system. If you already done that, or further modifications, then you should try to do a completely fresh install and try this method.

During install I used &quot;guided partitioning&quot; and "Full disc encryption with LVM".

Hope this works for you also!

---

