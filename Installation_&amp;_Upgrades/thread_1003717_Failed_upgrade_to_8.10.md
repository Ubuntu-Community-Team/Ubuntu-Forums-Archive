---
title: "Failed upgrade to 8.10"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by Raedwald on 2008-12-06
Youngest son has run an upgrade of his system fromn 8.04 to 8.10.

Something, however, went very wrong, and the upgrade failed. Exactly what the errors were I can't say as I wasn't around when he did this. However, I think the problem was down to insufficient free space on the Primary Windows drive. Whatever, selecting Ubuntu from the boot menu gives an immediate "file not found" error. Win XP boots fine, however.

I've managed to free up about 3.5Gb on the drive, so there's plenty of free space now.

So, is there any way of recovering/repairing from this mess other than a complete reinstallation of 8.10 (which is like as not going to lose a fair bit of his /HOME)?

---

### Post by inobe on 2008-12-06
when you try to run 8.10' how far does it get, also when it gets there' what happens, any errors too ?

---

### Post by Raedwald on 2008-12-06
Immediately on selecting Ubuntu from the boot menu, the message "Error 15 File Not Found" is displayed.

I'm assuming that the upgrade hasn't copied files onto the primary windows partition, hence the failure.

---

### Post by inobe on 2008-12-06
that's something that definitely required a search, i have never experienced such an error, going by the search' not many are affected either.

[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

i am not saying that is a solution, i would google that error, also search the forums.

good luck

edit: here are the release notes for 8.10, compare the known bugs that apply to your hardware

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

---

### Post by inobe on 2008-12-06
someone posted this in one of the forums

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD)

---

### Post by Raedwald on 2008-12-07
So, if I follow that, a reinstallation of GRUB could solve the issues?

---

### Post by caljohnsmith on 2008-12-07
Reinstalling Grub will unfortunately not fix a "file not found" error when you try and boot Ubuntu from the Grub menu. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
ls -l /mnt/boot
cat /mnt/boot/grub/menu.lst
```
Note "-l" is a lowercase L, not a one; please post the output of all the above commands.

---

