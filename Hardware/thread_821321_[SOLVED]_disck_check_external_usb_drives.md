---
title: "[SOLVED] disck check external usb drives"
date: 2008-06-07
forum: Hardware
---

### Post by malaTG on 2008-06-07
Hi

I have a couple of external usb drives On my internal drives I have automated controls that check that my drives are ok. Is it possible to do the same for external drives?

/Marcus

---

### Post by Rocket2DMn on 2008-06-07
Are these tools that run in linux?  If your tools do filesystem checks, you should be able to do the same for both internal and external.  If the programs are specific to each piece of hardware, you may be able to.
Can you tell us what exactly it is that you are using and what file system types you are using them on?

---

### Post by malaTG on 2008-06-07
Thx for answering so quickly!

I just changed the last number on my disk in /etc/fstab from 0 to 1.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0a8812cf-3293-4c52-80ae-da62c6e8fa99 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=092277ce-66cc-44b3-86b8-563486ddd6b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=f39f7a6b-d667-42ab-9e51-0c3083316585       /mnt/inspelningar   jfs   rw 0   0
UUID=915c2ebe-5f4a-4b14-8df7-148340acd3cd       /mnt/intern_250GB   ext3  rw 0   1

Is there tools for doing this? And another question that appeared now, can I have disk check on jfs file systems also?

My external drives are ext3 and fat32.

---

### Post by Rocket2DMn on 2008-06-07
You should have it as number 2 instead of 1 - the root filesystem should be the only partition that has a pass value of 1 (this is the order in which filesytems are checked for errors during the boot sequence when fsck runs).  I'm not entirely sure if linux can check JFS file systems, I think it might just be a UNIX thing, though support can probably be added to linux for it.
You can check fat32 partitions using fsck.vfat.

---

### Post by malaTG on 2008-08-29
Okey I changed my settings in fstab so that my internal second drive has a 2 instead of a 1.

However I still have external drives that are automagically mounted under media. When I look in my system log I see that it says that my external drives needs to be checked. 

> [  105.233594] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended


Is there anyway to get this automatically done?

/mala

---

### Post by Rocket2DMn on 2008-08-29
That means that the filesystems has been mounted X number of times and, for general health reasons, should be fsck'd.  Did it not prompt you to run the filesystem check when you plugged the drive in?  If it's not asking you to fsck, then I'm sure you could write a script to do this for you, but I don't know how exactly.  It may not prompt because the drive is external and assumes you want to use it right when you plug it in.  You CAN change the number of mounts between fsck's though, using tune2fs.

---

### Post by malaTG on 2008-08-29
Ok just to sum up

I basically always have my external drives connected but there is no setting anywhere so that I can get them automatically checked, at boot for instance, without writing a script for it?!

Thank you for your help again Rocket2DMn!

---

### Post by Rocket2DMn on 2008-08-29
Since you always have the externals plugged in, you could add fstab entries for them, and add that "2" to the pass column in fstab.  For some info on using fstab, see [uhelp]community/Fstab[/uhelp]
If you need some help setting up fstab entries, post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
Then please point out which devices are your externals and tell me where you would like them mounted (no spaces in the mount point, please).

---

### Post by malaTG on 2008-08-30
Thank you for your help!

I decided to mount my external disks in fstab and now every disk is checked regularly. 

Just to answer an earlier question, the JFS file system is also checked.

---

