---
title: "NTFS moutns in gnome, not KDE"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by robertsaron on 2007-04-22
I have 3 hard drives, sda1=xp pro, sdb1=ubuntu feisty, and sdc1=back/storage drive.

I installed feisty then decided to use sdc1 as another linux drive, so wiped it clean. When modding my mtab and fstab, do i need to add the drive into both or just one or the other? Also if I load gnome first, its sees my windows disk and I can then read it in KDE. If I load KDE first, it sees it, mounts it, but gives me a user id error 1000.

I want to auto mount both drives in KDE, and be able to set read/write permissions for my sdc1 drive. Below is a copy of my mtab and fstab files:

MTAB:
/dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0

FSTAB:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=b5b2f408-e7d1-49a7-92ec-5724d26e44cc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=b9f9675b-746b-48ed-92a8-19d427d4e1d6 none            swap    sw              0       0
/dev/sdc1       /media/storage    ext3     auto    rw,user,exec,sync       0       0
/dev/hda        /media/cdrom0              udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0             auto    rw,user,noauto  0       0

I just want to be able to read my windows drive and have it auto mount. How do I get my drives to auto mount with read/write permissions on the sdc1?

I have looked on the net, and am at loss. What do the different numbers mean at the end? Also, if I log out of KDE and then back in, does that reload the fstab and mtab, or do I need a full reboot if changes are made to them. 

Does linux have a repair feature like windows, but can reset the system like it was at time of install? Many thanks

---

### Post by fer3008 on 2007-04-29
the same happens to me, if i start kde after gnome the disks are there but if i start kde as my first log in
im not being able to see my ntfs and fat32.

someone can help with this one?

thanks

---

