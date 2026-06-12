---
title: "Jaunty installation headache"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-06-07
Had Intrepid on my desktop and upgraded to Jaunty but this was unsatisfactory so I decided to re-install Jaunty from the live CD.

Tried to keep everything "as is" but reformatted the device with the / folder. Setup finished without a hitch, but when I restarted, absolutely nothing. The GRUB loader worked (it is a dual boot setup, also has Windows XP), I choose Ubuntu, hit "ENTER", and then the screen goes blank. Nothing else happens.

When I boot to the live CD, is there a way I can see the partitions, directories, files, etc. so I know they're still there?

If I open a terminal window and type "sudo fdisk -l" I can see all the devices and drives.

The command "sudo fdisk -l /dev/sdc12 gives the following:

sudo fdisk -l /dev/sdc12

Disk /dev/sdc12: 19.8 GB, 19847568384 bytes
255 heads, 63 sectors/track, 2412 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc12 doesn't contain a valid partition table


sdc12 is where my / folder is located.

Any hints or suggestions?

Thanks in advance from a desperate linux user.

---

