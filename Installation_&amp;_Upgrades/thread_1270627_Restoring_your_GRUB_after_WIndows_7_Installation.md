---
title: "Restoring your GRUB after WIndows 7 Installation"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by darksoul7 on 2009-09-19
HELP! WINDOWS OVERWROTE MY GRUB!!!! &#8211; A How-To for Ubuntu 9.04 and similar

So you just did a fresh install of Windows and now, GRUB loader is gone. Here is a way to reinstall your GRUB loader without having to reinstall Linux &#8211; 

First, boot from your LiveCD
Open Terminal and type:
```
sudo fdisk -l
```

You will get something like this:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31026   249212832    7  HPFS/NTFS
/dev/sda3           31027       59463   228420202+   f  W95 Ext'd (LBA)
/dev/sda4           59464       60801    10747485    7  HPFS/NTFS
/dev/sda5           41225       59463   146501632    7  HPFS/NTFS
/dev/sda6           40496       41224     5855661   82  Linux swap / Solaris
/dev/sda7           31027       40494    76051647   83  Linux
```
Find your Linux partition (in this case, it&#8217;s /dev/sda7) and make note of it.

Next, you need to find the GRUB ID. 

In Terminal, type:
```
gksu gedit /boot/grub/device.map
```

A window will pop up with something similar to this:
```
(hd0,1) /dev/sda1
(hd0,2) /dev/sda3
(hd0,3) /dev/sda4
(hd0,4) /dev/sda5
(hd0,5) /dev/sda6
(hd0,6) /dev/sda7
```
Find the ID that corresponds to the partition ID of your Linux installation (in this case, hd0,6) and make note of it
Close the window and type the following in Terminal:
```
sudo grub
```
Press Enter and type:
```
root (hd0,6)
```
Be aware that you must put in the proper GRUB ID found in the device.map.
Press Enter and type:
```
Setup (hd0)
```
Reboot.  You should now have GRUB back!

---

