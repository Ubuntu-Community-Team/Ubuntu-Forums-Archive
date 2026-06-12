---
title: "Can't boot after wiping secondary hard drive"
date: 2008-09-28
forum: General Help
---

### Post by bostonbrawla on 2008-09-28
Hi All,

So I wiped what I thought to be just a secondary hard drive, but didn't realize grub was installed on it.  I had created a new ubuntu 8.0.4 installation on my larger drive to take advantage of 64 bit and encrypted partition.  Ubuntu was on both drives and I used fdisk to wipe the smaller of the two.  On boot, the computer couldn't find grub and wouldn't boot to my new install.  
Been troubleshooting for a while so here are some things I've done.  Re-installed Ubuntu on my second drive.  Grub would then auto boot into that install and not give the option to boot into the new one.  I then tried to use Super grub and changed the active partition and fix grub on the larger drive (/dev/sda1).  After doing this, grub shows both options on boot, but when choosing any of them I get Error 15: File not found.
I then looked at what grub was accessing when trying to boot (e from menu), and saw /boot/vmlinuz... did not exist as the boot directory was not there.  I manually mounted /dev/sda1 and created the boot directory and copied the contents of / to /boot (/ contained the vmlinuz files, etc).  Now on boot ubuntu will start to load and asked me for my encyption password, but goes to a command line.

Here is the output of fdisk -l.

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48924891

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       12188    97651102+   5  Extended
/dev/sda5              32       12188    97651071   83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2127bf58

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris

Appreciate the help!

---

### Post by caljohnsmith on 2008-09-28
Do you know which of your two HDDs you are booting from on start up? Which Ubuntu do you want to control the MBR (if you have a preference)? Boot your Live CD, open a terminal, and please post the output of:
```
sudo mkdir /mnt/sda1 /mnt/sda5 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda1 /mnt/sda5 /mnt/sdb1
cat /mnt/sda1/boot/grub/menu.lst
cat /mnt/sda5/boot/grub/menu.lst
cat /mnt/sdb1/boot/grub/menu.lst
```
That will make it clearer what your setup looks like at this point.

---

