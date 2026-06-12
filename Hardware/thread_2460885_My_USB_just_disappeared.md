---
title: "My USB just disappeared"
date: 2021-04-20
forum: Hardware
---

### Post by v-1-n-a-s-a-k-a on 2021-04-20
I was using the "Disks" ubuntu utility and I was formatting the only partition that there is/was on my USB drive, the case is that I did not put any name to the partition, but I did not notice it until it was too late.
The USB formatted as usual but when it finished, an error screen popped up saying something like "formatting unsusccessfull"
And now, that USB drive does not appear anywhere, even if the LED of the USB is on (meaning that is not a problem of the USB drive itself).
I try running fdisk but it still does not show. So that is all, how can I get back (if it is possible) my lovely USB?.
Btw, sorry for my bad English:P and thanks you all in advance :D.

---

### Post by ipv2 on 2021-04-20
> **v-1-n-a-s-a-k-a said:**
> the LED of the USB is on (meaning that is not a problem of the USB drive itself).

if the led on a flash drive is on it means the flash drive is not dead but the software could be corrupted which makes the flash drive practically useless.

---

### Post by ajgreeny on 2021-04-20
I have never used disks to format a disk of any sort, always using gparted which has been my choice for very many years.
Did you delete the partition on the USB before formatting or simply choose to reformat the partition?

I suggest you install gparted on your installed system and run that with the USB attached.
At top right of the gparted window there is a dropdown box where you can choose the device you wish to see.
Does your USB disk show there?
What partitions, if any does it show on the USB?
Perhaps there are no partitions on the disk.
I am aware that it is possiblr to format a device, eg /dev/sdb, using Windows, as opposed to a partition, eg /dev/sdb1, but I'm not sure if the same is possible in Disks, having never used it.  However gparted will tell us a lot more about the disk hardware, I think, so tell us what it shows.

---

### Post by ipv2 on 2021-04-20
> **ajgreeny said:**
> I'm not sure if the same is possible in Disks, having never used it.

disks will give you three options to format :

1. ext4

2. ntfs

3. fat

---

### Post by ajgreeny on 2021-04-21
> **ipv2 said:**
> disks will give you three options to format :

1. ext4

2. ntfs

3. fat
Yes, but that is all about the filesystem used not the device on which you create it!

---

### Post by ipv2 on 2021-04-21
> **ajgreeny said:**
> Yes, but that is all about the filesystem used not the device on which you create it!

disks also gives the following information about a flash drive :

Size

Device

UUID

Partition Type

Contents

---

