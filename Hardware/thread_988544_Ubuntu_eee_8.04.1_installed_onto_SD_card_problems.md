---
title: "Ubuntu eee 8.04.1 installed onto SD card problems"
date: 2008-11-20
forum: Hardware
---

### Post by Gabriel Knight on 2008-11-20
Hello all,

I'm a Windows Guru, and a Linux newbie. I have an Asus eee 900 notebook. I have Windows on the main SDD and don't want to touch that, so I used a USB drive to bootup and install Ubuntu onto my SD card. I used a distro designed specifically for the eee.

The problem I'm encountering seems to be not an unknown one, but I haven't found any specific resolutions to fix everything. Basically, it seems that when the installation is done, the system reports the SD card with a different designation than once it is done, and you bootup using the SD card. Using the eee's bootup option you can choose to boot from the SD card. Once this is done, then the system seems to report the card as hd0,0.

I have Ubuntu running, and I've been able to modify the device.lst in the boot/grub directory so it chooses the correct location to start the bootup. However, most of my software won't run, I cannot view updates, cannot get into most configuration sections... the most common error that I get is 
"Unable to copy the user's Xauthorization file."

But very often I don't even get this, just nothing happens. For example, if I try to launch Firefox, nothing happens. If I click on the update icon and select "Show Updates" nothing happens.

I WAS getting the "xauthorization file" error before if I tried to launch package manager, but now after a reboot I am for some reason able to get into it. However, I still cannot get into most things.

My suspicion is that there may be some parts of the system that are still trying to address file locations using the wrong designation for the SD card. I could be wrong. 

Either way, I'm really stuck because I'm a total amateur at Linux. So, anything I can post further information or tests/results etc. please help! any assistance is very much appreciated.

---

### Post by Gabriel Knight on 2008-11-20
*correction: file modified is menu.lst not device.lst

---

### Post by Gabriel Knight on 2008-11-21
bump.
Any ideas anyone?

---

