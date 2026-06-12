---
title: "32 G flash drive challenge"
date: 2011-03-30
forum: Hardware
---

### Post by ELMIT on 2011-03-30
I got a 32 G flash drive (USB-3) and plugged it into my EeePC.

It will be recognized and is functional - it seems.

I have in mind to replace my files for VirtualBox from 250G hard disk to this flashdrive.

I encounter some troubles:
mtab showed me the drives (250G hard disk and flash drive) as:

> /dev/sdd1 /media/Ron-250G fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sde /media/ADATA\040UFD vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush 0 0

Following problems come up:
1. file names with capital or small letters are recognized as the same.
2. File size is max 4GB.
3. the flash drive is recognized as /dev/sde not sde1 !!!!


How to solve that?

bye

Ronald

---

### Post by gordintoronto on 2011-03-30
I'm sorry, but I don't understand the problem. What do you want help with?

Bear in mind that a USB flash drive is much slower than a hard drive.

If you want files larger than 4 GB, format the flash drive as NTFS. Gparted can do this.

---

### Post by oldfred on 2011-03-31
You may have it formated as a floppy disk, so it does not have partitions, just a root. I think exfat can be that way, but I thought exfat did not work in Ubuntu.

What does Gparted show.

Ubuntu is case sensitive, but windows is not. So you can have issues in FAT & NTFS if you write two files with same name but with the only difference is case. Windows will then get very confused.

---

