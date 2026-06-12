---
title: "Problems with segate 200Gig dirve"
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by NoJock on 2006-02-08
Hi: All 
[COLOR="Magenta"]**Im not even a bean yet just a bud not even a flower a real new bee.**[/COLOR]
I do like this forum. Im working on another problem and really dont know what to do.
when i boot from the live CD my 3 CD drives load properly and my usb 1Gig flash drive also loads. All the above devices are accessable. The problem is my segat drive is not on the desktop with all the outhers.

Have run the sudo fdisk -l and its there, but have no idea how to mount it. 
                                  Results
/dev/sda1 *    1      3916  1002480        e win95 fat 16 LBA     Think this is my flash drive
Disk /dev/hda : 200.0GB , 200049647616 bytes
240 heads, 63 sectors.track , 25841 cylenders
Units = cylinders of 15120 * 512 = 7741440 bytes  
/dev hda1 *    1      6329  47847208+   c win95 fat 32 LBA       Think this is first partition on hard drive
/dev/hda2    6330  25841 147510720    f win     ext'd   LBA       Think this is ????? unknown
/dev/hda5    6330  25841 147510688+ 7  HPFS/NTFS               Think this is second partition on hard drive
                    cat /etc/fstab
/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid , no dev 0 0

If i didnt make a mistake with any thing this should be correct, dirve was formated under XP and only has two partitions so im not sure where hda2 came from.
all works under windows and would like to see hda1 on the desk top dont mind typing in cmd's untill all issues are resolve before installing along with win XP pro.
Thansk and any help would be absoultly great.:cry:

PS: my floppy doesn't show up either, nor work.

---

### Post by lha on 2006-02-10
[QUOTE=NoJock]Hi: All 
[COLOR="Magenta"]**Im not even a bean yet just a bud not even a flower a real new bee.**[/COLOR]
I do like this forum. Im working on another problem and really dont know what to do.
when i boot from the live CD my 3 CD drives load properly and my usb 1Gig flash drive also loads. All the above devices are accessable. The problem is my segat drive is not on the desktop with all the outhers.

Have run the sudo fdisk -l and its there, but have no idea how to mount it. 
                                  Results
/dev/sda1 *    1      3916  1002480        e win95 fat 16 LBA     Think this is my flash drive
Disk /dev/hda : 200.0GB , 200049647616 bytes
240 heads, 63 sectors.track , 25841 cylenders
Units = cylinders of 15120 * 512 = 7741440 bytes  
/dev hda1 *    1      6329  47847208+   c win95 fat 32 LBA       Think this is first partition on hard drive
/dev/hda2    6330  25841 147510720    f win     ext'd   LBA       Think this is ????? unknown
/dev/hda5    6330  25841 147510688+ 7  HPFS/NTFS               Think this is second partition on hard drive
                    cat /etc/fstab
/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid , no dev 0 0

If i didnt make a mistake with any thing this should be correct, dirve was formated under XP and only has two partitions so im not sure where hda2 came from.
all works under windows and would like to see hda1 on the desk top dont mind typing in cmd's untill all issues are resolve before installing along with win XP pro.
Thansk and any help would be absoultly great.:cry:

PS: my floppy doesn't show up either, nor work.[/QUOTE]

An ide drive can have only 4 primary partitions. To make partitioning a bit more flexible, one of those partitions can be made extended. That hda2 you see is an extended partition. It can contain multiple logical partitions. This allows you to have more than 4 partitions on one hard drive. Think it as a container for hda5. Hda5 is a logical partition and hda1 is a primary. Windows usually wants to have one primary partition and it creates other partitions it creates are logical. This doesn't prevent you from making additional primary and/or logical partitions for linux.

Try
```
sudo mkdir /media/drive_c
sudo mount /dev/hda1 /media/drive_c -o ro
```
and
```
sudo mkdir /media/drive_d
sudo mount /dev/hda1 /media/drive_d -o ro
```
to get those partitions visible. That '-o ro' makes those partitions read-only, just in case. (Only fat32 can be mounted read/write, ntfs is always read-only. If the other is fat32 and you want to write to it, remove that '-o ro' bit.)

Do you have a floppy in your floppy drive? Put one in and take a look at "Places->Computer->Floppy Drive".

---

### Post by NoJock on 2008-07-21
Solved upgraded to ubuntu 6.06

---

