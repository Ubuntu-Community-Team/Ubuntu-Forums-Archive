---
title: "[SOLVED] Cannot mount hibernated hard drive"
date: 2008-07-29
forum: General Help
---

### Post by Snowmatts on 2008-07-29
Alright I'm really new to Ubuntu

First I was in windows and i wanted to install ubuntu on a flash drive because my hard drive is only 40GB and ubuntu took up to much space. So to "uninstall" ubuntu i used the Disk managment utility from windows to remove the partition, which just made it unallocated. So I rebooted and my GRUB bootloader said "error 22" so i booted up into a live version of ubuntu on a cd and ran the command 

dd if=/dev/null of=/dev/hda bs=446 count=1

then i went into GParted and made my hard drive on partition again. I rebooted and got just a flashing line at the top left hand corner of the screen. So i went back to the live cd and try to mount my hard drive but it gave me an error message saying 

Windows is hibernated, refused to mount. Failed to mount '/dev/hda1': Operation is not permitted The NFTS partition is hibernated. Please resume windows and shutdown windows proberly so that mounting could be done safely.

How can i boot back into windows again

thanks

---

### Post by warp99 on 2008-07-30
You can use your Windows install disk to restore its bootloader to the MBR. Windows should then boot to the first NTFS partition.

---

### Post by Snowmatts on 2008-07-30
> **warp99 said:**
> You can use your Windows install disk to restore its bootloader to the MBR. Windows should then boot to the first NTFS partition.

Thanks for the help, but Toshiba didn't give me a windows install disk. They just gave me an "recovery cd" that reformats the whole hard drive. Something that I am really trying to avoid

---

### Post by Mgiacchetti on 2008-07-30
Get [this]("http://www.ambience.sk/experiments/MbrFix.exe") and put it in a windows boot disk.

Boot from the disk
at a:\>
Run MbrFix to see the current list of partitions: ```
mbrfix /drive 0 listpartitions
```Run MbrFix in the following way: ```
mbrfix /drive 0 fixmbr
```If you have more than 1 physicial hard disk (hard drive), you have to use proper number for your disk. E.g. change 0 to a different number (1, 2 etc.)

[B]
-----------OR-----------

sudo apt-get install ms-sys

[/B][B]sudo fdisk -l 
[/B]which will return something like ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7762    62348233+   7  HPFS/NTFS
/dev/sda2            7763       17956    81883305   83  Linux
/dev/sda3           17957       18338     3068415   82  Linux swap / Solaris
/dev/sda4           18339       19457     8981280    c  W95 FAT32 (LBA)

```find your ntfs disk (windows)

**ms-sys --mbr /dev/sdX **

where /dev/sdX is your windows disk in my case sda1 (sda = sata drive a || 1 = partition 1)

---

### Post by Snowmatts on 2008-07-30
Thanks for the response

When tell me to put mbrfix into a windows boot disk, how do i do that and what is a windows boot disk. I googled it and from what is saw it looked like it was a floppy disk. I don't have a floppy drive in my computer

And when i run sudo apt-get install ms-sys i get:
Couldn't find package ms-sys
So i tried to download it from sourceforge and extract and make it from the source code but when i run the command "make" i get a whole lot of errors.

I don't know if it matters or not but now i am running Ubuntu 7.10 on a 1gb flash drive.

Again, Thanks for the help

---

### Post by Snowmatts on 2008-07-30
Never Mind, i just had to enable all the repositories.It worked
Thanks so much for your help

---

### Post by Mgiacchetti on 2008-07-30
yep...  another thing, you can make a windows boot disk on a cd  [Bootdisks](http://www.bootdisk.com), or get the ultimate boot disk (ubcd).

---

