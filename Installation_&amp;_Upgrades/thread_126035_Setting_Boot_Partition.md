---
title: "Setting Boot Partition"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by jonathansizz on 2006-02-05
Hi

I've looked through the forum but none of the methods described seems to be quite what I am looking for. I have Ubuntu 5.10 as my main distro. I installed this first. Later I installed 6.04 preview, and this installed its own GRUB. Now, I want to remove 6.04 altogether but when I tried this GRUB no longer booted my system (presumably as it was looking for the no-longer-existant GRUB from the deleted 6.04 partition). So I reinstalled 6.04 in order to be able to boot into 5.10. What I need is to be able to remove 6.04 but have GRUB boot 5.10 (from the 5.10 partition?). Here is the relevant info:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 14797 19457 37439482+ 83 Linux
/dev/sda2 1 14216 114189988+ 83 Linux
/dev/sda3 14217 14796 4658850 5 Extended
/dev/sda5 14217 14594 3036253+ 82 Linux swap / Solaris
/dev/sda6 14595 14796 1622533+ 82 Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$


I think 6.04 is on sda1 and 5.10 is on sda2. So I think I need to have the asterisk next to sda2? sda5 is the swap for 5.10 and sda6 is the swap for 6.04

What is the best way of fixing this?

Thanks for your help!

---

### Post by GreyFox503 on 2006-02-05
If you have a liveCD like Ubuntu or Knoppix, try running it.  From there you can delete the partition you don't want, and run 'grub' or 'grub-install' to fix grub.  I don't remember the specifics of using these commands, though.

BTW:  For future reference, your system only needs one linux swap partition, not one for each OS.  They can all share it. :)

---

