---
title: "Grub stuck on flash drive!"
date: 2009-01-17
forum: Hardware
---

### Post by dpmanthei on 2009-01-17
Hi everyone, first post here,

Just like everyone else, I apologize if this is a noob question.  I have been using mandriva 2008 Spring, ubuntu 8.04, and now Mint 6 Felicia all for about a year total.  During a troubleshooting attempt on another computer, I installed Ubuntu on an 8GB Patriot flash drive successfully and fixed my issue.  I then formatted the flash drive to use it for data again.  Works great, HOWEVER, if the flash drive is in the computer when I start it, I get a Grub error 17...it seems that some or all of the grub boot loader is stuck on the drive.  I tried formatting (tried ext3, fat32, and xfs each), partitioning, and then formatting on a windows machine too.

How can I get it off?  Or even re-install grub so I can at least make an OS selection?  Thanks for any help!!!!

Dylan
------------
Intel DP45SG
2x2GB G.Skill DDR3 1333
Intel Q6600
ATI 4350 HD (512)

---

### Post by caljohnsmith on 2009-01-17
You could try zeroing the boot code in the MBR of the flash drive, and also remove the boot flag from any partition on that drive, and then your BIOS will probably skip over that drive and boot your HDD on start up instead. But the problem is that when some BIOSes skip booting the first drive in the BIOS boot order (hd0), then when they boot the next drive, that drive is still considered (hd1) or second in the BIOS boot order. That can cause problems with Grub depending if your menu.lst uses "root (hdX,Y)" notation instead of the newer UUID notation. But it certainly couldn't hurt to try, so if you want to give it a shot how about doing:
```
sudo dd if=/dev/zero of=/dev/[COLOR="Red"]sdX[/COLOR] bs=440 count=1
```
And replace "sdX" with your flash drive. Next check that no partitions are marked as bootable on that drive:
```
sudo fdisk -lu
```
And make sure none of the partitions on the flash drive have an asterisk * under the boot category. If so, you could do:
```
sudo fdisk /dev/[COLOR="Red"]sdX[/COLOR]
```
Press "a", then give the partition number of the partition with the boot flag, then do "w" to write the changes. Next reboot and let me know how it goes. :)

---

