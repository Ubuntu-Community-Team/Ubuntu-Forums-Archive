---
title: "hibernation does not work after repartitioning and re-adding swap"
date: 2008-08-11
forum: General Help
---

### Post by shjoity on 2008-08-11
8.04 K7S5AP

the uuid of my swap changed after i did a little reformatting. after it freezing on running hibernate.sh i readded the swap and it now mounts on boot, (4GB, mem=1GB) hibernate.sh now works but the computer does not realize the computer was hibernated and continues on to a normal boot.

how do i get the kernal to recognize the computer has been hibernated???/what partition to lok at?

fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9307113

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2675    21486906   83  Linux
/dev/sda2   *        2676        3891     9767520    7  HPFS/NTFS
/dev/sda3            3892        9470    44813317+  83  Linux
/dev/sda4            9471        9729     2080417+  82  Linux swap / Solaris


fstab

# /dev/sdb2
#UUID=31cb549a-e894-492a-8423-90083cb7f212
# /dev/sda4
#UUID=4f9d51f0-9cc2-4fba-a5da-f5884f344ae3 
/dev/sda4	none            swap    sw              0       0

---

### Post by jimv on 2008-08-11
Use "sudo blkid" to get the new uuid for your swap partition, then update your /etc/fstab file with the new uuid.

---

### Post by logos34 on 2008-08-11
> **shjoity said:**
> now works but the computer does not realize the computer was hibernated and continues on to a normal boot.


I have to use the following option on my 'kernel' line in /boot/grub/menu.lst:

> kernel  /boot/vmlinuz-2.6.24-19-rt root=UUID=xxxx...  ro splash **resume=/dev/sda8**


---

### Post by Taxman415a on 2008-08-11
Following coffecat's first post in this thread: [http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565) you should use the -c /dev/null option to blkid and edit /etc/initramfs-tools/conf.d/resume to include the new correct uuid in addition to fstab.

---

