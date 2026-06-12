---
title: "Half of my 300gb disk is useless?"
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by chimera on 2005-12-27
[_Screenshot_](http://freeweb.siol.net/klemenf1/qtparted.jpg)

I can't resize any partition besides swap, and I can't create a new partition in the empty space, even though I've started qtprated with sudo. Is there anything I can do besides trashind my HD and getting a new one?

[COLOR="LightBlue"][SIZE="1"]and yes I know I have an oversized NTFS partition[/SIZE][/COLOR]

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-27
You have four primary partitions. You cannot have more than that, so the rest of the drive cannot be accessed. Delete the swap partition, then create new logical partitions to fill the rest of the space. It works the same way, just answer "logical" when it asks if the new partition you want to create is "primary or logical?"

---

### Post by chimera on 2005-12-27
but I just want to resize the existing partitions, and it won't let me do that either:confused:

btw

whenever I try to umount /dev/hda4 (which is swap) it says

partition is not mounted (according to mtab)

but when I try to delete it in qtparted it says

partition is mounted

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-27
You cannot resize the partitions you have because the data will get overwritten. If you were to "resize" hda2, for example, you would obliterate the data at the beginning of hda3. And are you trying to do this from ubuntu? You cannot do that when you have /home mounted and you cannot run gparted without /home.

What is it you want to do? If you want access to that extra space above /swap you will need to get it out of the way. Are you just trying to make /home use the rest of the disk?

In order to access the rest of that disk you have three choices:

reinstall ubuntu and partition it properly this time

remove the /swap line from your /etc/fstab, reboot, obliterate that partition and grow /home over it then add a new partition for /swap above that.

remove the /swap line from your /etc/fstab, reboot, remove the partition and create a new extended partition that fills the entire rest of the unused space and create logical drives within that extended space in whatever layout you want.

---

### Post by plors on 2005-12-27
Hi, as &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; stated your swap partition is the key. you can switch if off with swapoff /dev/hda4 and then remove it.

Create an extended partition in the unallocated (free) space and recreate your swap partition in that extended partition. Then go ahead and create any number of partitions you like.

To avoid possible problems you could start gparted from a livecd instead of your live system.

don't forget to update your /etc/fstab afterwards since your swap partition will be most likely at /dev/hda5 instead of /dev/hda4

cheers...

---

### Post by chimera on 2005-12-27
Well, I reinstalled it, I copied all my files from the old /home partition (20gb) to the new one(100gb) so nothing is lost:D thanks for the help guys!

---

