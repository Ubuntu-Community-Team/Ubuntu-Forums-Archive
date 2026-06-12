---
title: "grub-install errors (probably device.map problem)"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by gluonman on 2009-11-02
Hi. I'm trying to setup a dual-boot with Ubuntu 9.10-amd64 and Windows 7 (64-bit) on a Lenovo ThinkPad W700. It's for work, and my boss has requested Ubuntu on the first partition (faster part of the disk). So, having installed Ubuntu first, I need to reinstall grub on the /boot partition since Win7 replaced it after it got installed. I'm booted into the Ubuntu liveCD and have attempted many times to use the grub-install script to install GNU GRUB 1.97~beta4. The errors I'm getting seem to point to an ultimate problem with my device.map. I'm not entirely sure what to do from here.

   To assist you in helping me, I've provided the following information, including examples of the errors I'm receiving:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x777aa0e1

   Device Boot      Start         End      Blocks   ID  System
/dev/sda1               1          62      497983+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              63        7478     59569020  83  Linux
/dev/sda3            7479       15380     63472815   5  Extended
/dev/sda4   *       15381       30402    120656896   7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5            7479       14894    59568988+  83  Linux
/dev/sda6           14895       15380     3903763+  82  Linux swap / Solaris
ubuntu@ubuntu:~$cat /boot/grub/device.map
(hd0)   /dev/sda
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ sudo grub-probe -t device /boot
grub-probe: error: cannot find a device for /boot.

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/boot /dev/sda
grub-probe: error: cannot find a device for /boot/boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$
```

   As far as post-installation conditions are concerned, Win7 works fine, and since I haven't been able to install grub yet I haven't had the chance to test Ubuntu and see if it's still intact. This is actually my second attempt, and the first time I did this my only noticeable problem was that my mousepad stopped working in Ubuntu.
   I'm sure you also noticed the messages in the fdisk -l output concerning a couple partitions not ending at the cylinder boundaries. Should I be concerned about that?
   Please help me figure out how to get grub installed so I can move on and test Ubuntu and make sure my dual-boot setup is legitimate. I would truly appreciate the assistance.

---

### Post by robophred on 2009-11-04
I have an identical issue, minus the partitions not aligned.

I think the issue is that the grub commands assume they are being used from the operating system you want to link, and it cannot work for the livecd.  I got grub-install to return "sucessful" by using
sudo grub-install --root-device=/mounted/grub/partition /dev/sdb
but this apparently is not writing the MBR to my second disk as I expect.

grub-update does not have any option to set the root device.  I tried chrooting, but chroot throws command not found no matter what command I enter.

---

### Post by longlegs on 2009-12-27
When synaptic 'installs' grub, it does'nt. You have to use apt-get grub-install (or apt-get install grub?) which does install grub. 
Also looks like you did not mark a partition as / when you formatted the disk or when you installed ubuntu. Use the live cd, start partition editor (qparted?) and edit the linux partition, mark to be used as /, DO NOT FORMAT.
Good luck.
ps I am surprised there were no replies to your problem.

---

### Post by presence1960 on 2009-12-27
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

