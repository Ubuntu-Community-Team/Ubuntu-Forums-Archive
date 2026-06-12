---
title: "&quot;Invalid Partition Table&quot; CD error for attempted installation"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by David Miller on 2008-12-12
I attempted to install Ubuntu 8.10 on a laptop that was a Sony running Windows XP (Sorry, no more details)

The boot CD seemed to be working well & I had gotten past the options for location/name etc.

After about 39% of the installation bar, an error came up saying that there was an error on the CD. so I powered off & burnt a new CD.

When I power up the laptop now, I get the following message:

[INDENT]For Realtek RTL8139(A/B/C)/RTL8130 PCI Fast Ethernet Controller v2.11 (001205)
PXE-E61: Media test failure, check cable
PXE-MOF: Exiting PXE ROM.
Invalid partition table[/INDENT]

The new boot CD seems to have no effect.

All I can find referencing "Invalid partition table" is situations where there has been a dual install.

If anybody has any help that would be great

Thanks

---

### Post by wpshooter on 2008-12-12
Did you/are you checking the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by caljohnsmith on 2008-12-12
Unfortunately, it sounds like the installer might have left your partition table corrupt; how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo sfdisk -l
sudo fdisk -lu
sudo parted /dev/sda print
```
Then make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen, and we can work from there if you want. :)

---

### Post by impact on 2008-12-12
The system cannot boot from the HDD so it tries to boot from the network... and fails, too. 

[http://www.asklaptopfreak.com/laptop-notebook-help/2006/07/06/pxe-e61-failure-error-when-booting/](http://www.asklaptopfreak.com/laptop-notebook-help/2006/07/06/pxe-e61-failure-error-when-booting/)

Reboot the machine, enter setup, disable booting from the network and change the boot order so that it boots from the CD first. 

Then boot from a known GOOD CD, and use the tools to fix the mess and reinstall.

---

### Post by David Miller on 2008-12-12
I didn't check before my initial attempt. - So now I know to do so in future.

The first CD I burnt (the one that got part-way through the install) has an error when I run the check integrity and suggests I burn another.

The second CD has no issues when I run that check.

---

### Post by David Miller on 2008-12-12
There was only one reply when I wrote the last post - thanks for your time folks: 

When I power up the machine I go straight to this screen, without any options to enter a setup mode - how should I go about doing this?

---

### Post by caljohnsmith on 2008-12-12
> **David Miller said:**
> There was only one reply when I wrote the last post - thanks for your time folks: 

When I power up the machine I go straight to this screen, without any options to enter a setup mode - how should I go about doing this?
So can you go into your BIOS and change it so that the CD drive will boot first? You want to look for "boot order" or some setting of that sort in your BIOS.

---

### Post by impact on 2008-12-12
Try pressing the F2 key repeatedly or holding it during boot, that should get you to the BIOS menu. If that doesn't work, try other common keys (F1, F3, Esc, Delete).

---

