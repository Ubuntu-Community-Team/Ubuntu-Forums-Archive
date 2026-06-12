---
title: "can't mount cloned disk, even with changed UUID"
date: 2012-09-05
forum: Hardware
---

### Post by jpvrla on 2012-09-05
I cloned my master disk (dual boot capable ,windows7 and unbuntu 12.04) to a slave via Acronis backup.   Everything boots fine but I want the ability to boot from either root partition (sda5 or sdb5) on a specific drive .   There are other similar posts but I find them short of answering some of my related questions.

Basically no matter what I do  the df command always lists /dev/sda5 as the mounted root device.   When I select a specific linux partition as listed by grub it always ends up with sda5 as the root partition.   I was able to assign a different UUID to the sdb5 root partition.  Yet, when I change fstab to mount it using this  UUID it still boots up mounting sda5.   I even changed all  the UUID entries  in /boot/grub/grub.cfg for sdb5 (by mounting  to a non- root mount point) and to my bewilderment sda5 still came up as the mounted root partition.   I did update-grub also.   

Why does all this appear to be so illogical?  Maybe I just have an old admin attitude about this but It appears to me that the fstab, UUIDs,  and grub2 are not on the same page.   Should I just resort to using the LABEL option? Thanks for any clarification or related experiences.

Particulars follow:
Linux MYpc 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 
x86_64 x86_64 GNU/Linux

Mypc:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x415564fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2   *      206848   682141922   340967537+   7  HPFS/NTFS/exFAT
/dev/sda3       682143742   976771071   147313665    5  Extended
/dev/sda5       682143744   969598975   143727616   83  Linux
/dev/sda6       969601024   976771071     3585024   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9999c5d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      208844      104391    7  HPFS/NTFS/exFAT
/dev/sdb2   *      208845   682119899   340955527+   7  HPFS/NTFS/exFAT
/dev/sdb3       682119900   976768064   147324082+   5  Extended
/dev/sdb5       682119963   969587009   143733523+  83  Linux
/dev/sdb6       969587073   976768064     3590496   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 3671 MB, 3671064576 bytes
255 heads, 63 sectors/track, 446 cylinders, total 7170048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x571d00f1

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table


[ USER ~ ] $ sudo findfs UUID=3e77c155-b7ab-419a-99dc-dddda79e7d51
/dev/sda5
[ USER ~ ] $ sudo findfs UUID=11999861-61c7-4fe9-96b5-f9a7db3f3fb7
/dev/sdb5

[ USER ~ ] $ cat /etc/fstab
proc            /proc           proc    nodev,noexec,nosuid 0       0
### sda5
###UUID=3e77c155-b7ab-419a-99dc-dddda79e7d51 /               ext4    errors=remount-ro 0       1
### sdb5
UUID=11999861-61c7-4fe9-96b5-f9a7db3f3fb7 /               ext4    errors=remount-ro 0       1
/dev/mapper/cryptswap1 none swap sw 0 0
tmpfs /dev/shm tmpfs defaults,ro 0 0

[ USER ~ ] $ df
Filesystem            1K-blocks     Used Available Use% Mounted on
/dev/sda5                                  143524252     26957844 109380028   20% /
udev                                                         1745420                           8         1745412        1% /dev
tmpfs                                                        703168                     956           702212       1% /run
none                                                                   5120                      0                 5120        0% /run/lock
none                                                         1757912                188         1757724       1% /run/shm
/home/USER/.Private 143524252 26957844 109380028  20% /home/USER

[ USER ~ ] $ sudo blkid
/dev/sda2: UUID="2999A6AA88A685BA" TYPE="ntfs" 
/dev/sda5: UUID="3e77c155-b7ab-419a-99dc-dddda79e7d51" TYPE="ext4" 
/dev/sdb2: UUID="2999A6AA88A685BA" TYPE="ntfs" 
/dev/sdb5: UUID="11999861-61c7-4fe9-96b5-f9a7db3f3fb7" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="4a32aa96-cd4b-4b9c-8880-7e1aab573fdb" TYPE="swap" 

[ USER ~ ] $ ls -al /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 120 Sep  4 23:14 .
drwxr-xr-x 5 root root 100 Sep  4 18:14 ..
lrwxrwxrwx 1 root root  10 Sep  4 23:14 11999861-61c7-4fe9-96b5-f9a7db3f3fb7 -> ../../sdb5
lrwxrwxrwx 1 root root  10 Sep  4 23:14 2999A6AA88A685BA -> ../../sda2
lrwxrwxrwx 1 root root  10 Sep  4 23:14 3e77c155-b7ab-419a-99dc-dddda79e7d51 -> ../../sda5
lrwxrwxrwx 1 root root  10 Sep  4 23:14 4a32aa96-cd4b-4b9c-8880-7e1aab573fdb -> ../../dm-0

---

### Post by oldfred on 2012-09-05
I am not sure which is which. Post link to BootInfo.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

It does not look like your clone has Windows in the same locations. The PBR - partition boot sector has embedded in it the start and size of the partition. If that does not match the partition table, Windows will not work. You may have to repair both sdb1 & sdb2 with chkdsk and/or BootRec.exe /FixBoot  and maybe the BootRec.exe /RebuildBcd commands as BCD has UUID type info also.

---

### Post by jpvrla on 2012-09-05
I tried running boot-repair and it asked if I wanted to update.   I went with the update but boot-repair ended spinning trying do a mount-ntfs.  Reluctantly ended up killing the process after allowing for 10 minute run.

As suggested, I decided to give the cloned ntfs filesystem, sdb2 a different uuid using the  dd command as suggested in the forum by another.  To my amazement I was able to boot the desired  linux root filesystem,sda5 or sdb5, and/or windows7 one either sda2 or sdb2.   Maybe the frontend running of boot repair corrected something but things are working as intended,ie, from grub mount the either the master or the clone root filesystem .  

Anxious to run software updates to see if sdb5 requires the same software updates as sda5.  Also keeping my fingers crossed to see what happens after the next kernel update.
Please close the case.

---

