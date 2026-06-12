---
title: "please... not much time! cannot get grub and win xp to boot correctly"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by jdstunner on 2009-09-14
I cannot get grub and win xp to play nicely. I have to go out of town tomorrow and I need to get this up and running fast!

There are three drives on my computer.

/dev/sda | /dev/sdb | /dev/sdc

My operating system files are installed on split partitions on /dev/sdc.

XP - /dev/sdc1
Ubuntu 9.04 - /dev/sdc2

There is another Ubuntu installation on /dev/sdb1. The swap partition is located on /dev/sdb2. There is a third ext3 partition used for data storage on sdb called sdb3.

/sda is a fat32 data partition. No OS. No boot configuration. 

I want Grub to load and show 5 options and be able to boot into each.

Ubuntu 9.04
Ubuntu 9.04 Recovery
memtest
Ubuntu 8.04
Win XP

On sdb, the grub installed on that drive is working great. All I want it to do is load Ubuntu so I can access my 900 GB media from any computer. If I set the BIOS to boot sdb first, this boot loader takes over and boots correctly. This is my backup OS. 

On sdc is where I am having the problems. 

sdc is split into two partitions as I mentioned earlier. Each is 80 GB. sdc1 is ntfs. sdc2 is ext3.

I set the BIOS to boot sdc. 
I installed XP first onto sdc1. Everything was working great. 
I installed Ubuntu. Grub loads, boots Ubuntu. 
Reboot. Grub loads, Win XP produces Error 13: Invalid or unbootable...
I use the XP Recovery Console and *fixmbr* to restore the win bootloader.
Reboot.
XP boots. No ubuntu.
Use Live CD and reinstall grub.
Reboot.
Grub boots. Cannot load XP. Boots Ubuntu.

Here is where I am stuck.

This is the code I used to reinstall grub:

```
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sdc2 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
find /boot/grub/stage1
root (hd2,1)
setup (hd2)
```/fdisk -l

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00010b2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    b  W95 FAT32

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000523f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2432    19535008+  83  Linux
/dev/sdb2            2433        2918     3903795   82  Linux swap / Solaris
/dev/sdb3            2919      121601   953321197+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ea02e9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS
/dev/sdc2            9729       19457    78148192+  83  Linux
```/boot/grub/menu.lst

```
title        Ubuntu 9.04 - MAIN OS
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title        Other operating systems:
# root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2 - MEDIADRIVE BACKUP OS
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
# This entry has been edited. Commented out lines are default. root and makeactive were added. 
title        WIN XP BLACK
root            (hd2,0)
makeactive
chainloader    +1
```NOTE: When I use, (which was the default grub entry)

 ```
rootnoverify    (hd2,0)
 savedefault
 map        (hd0) (hd2)
map        (hd2) (hd0)
```I get the same unbootable message.

---

### Post by oldfred on 2009-09-14
Please do not start two threads on the same issue. Answers get mixed and various people that are trying to help do not see the answers in the other thread.

Please also see my suggestion in your other thread in beginners.

---

### Post by presence1960 on 2009-09-14
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by oldfred on 2009-09-14
Presence,

I just found he had posted results.txt in a third thread which it looked like no one quickly responded to. I was having trouble figuring what thread I responded to so I did a search.

[http://ubuntuforums.org/showthread.php?t=1265928](http://ubuntuforums.org/showthread.php?t=1265928)

One more reason to have only one thread. As I know if Presence looks at the problem it can solve it. current working  thread
[http://ubuntuforums.org/showthread.php?t=1266012](http://ubuntuforums.org/showthread.php?t=1266012)

---

### Post by jdstunner on 2009-09-14
Sorry for multiple posts... please refer to thread

[http://ubuntuforums.org/showthread.p...75#post7948075]("http://ubuntuforums.org/showthread.php?p=7948075#post7948075")

---

