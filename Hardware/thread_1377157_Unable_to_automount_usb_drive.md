---
title: "Unable to automount usb drive"
date: 2010-01-10
forum: Hardware
---

### Post by pitchu on 2010-01-10
I'm unable to automount a usb device though I'm able to mount manually. Is there a command line utility that can be used to enable automount?

=================================================
I've enclosed some of the steps that I've tried

root@ubuntu:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   256876         0    256876   0% /lib/init/rw
varrun                  256876        44    256832   1% /var/run
varlock                 256876         0    256876   0% /var/lock
udev                    256876       124    256752   1% /dev
tmpfs                   256876         0    256876   0% /dev/shm
rootfs                 7734904    642176   6699812   9% /
root@ubuntu:~# mount /dev/sda1 /mnt/usb1
root@ubuntu:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   256876         0    256876   0% /lib/init/rw
varrun                  256876        44    256832   1% /var/run
varlock                 256876         0    256876   0% /var/lock
udev                    256876       124    256752   1% /dev
tmpfs                   256876         0    256876   0% /dev/shm
rootfs                 7734904    642176   6699812   9% /
/dev/sda1              1024496    142648    881848  14% /mnt/usb1

root@ubuntu:~# fdisk -l

Disk /dev/mmcblk0: 8050 MB, 8050966528 bytes
4 heads, 16 sectors/track, 245696 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x4fb442a5

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         123        3928   83  Linux
/dev/mmcblk0p2             124      245696     7858336   83  Linux

Disk /dev/sda: 1053 MB, 1053294592 bytes
2 heads, 63 sectors/track, 16327 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x009b23f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16328     1028592    b  W95 FAT32

root@ubuntu:~# uname -a
Linux ubuntu 2.6.30.2 #11 PREEMPT Wed Jul 22 19:53:31 MDT 2009 armv5tel GNU/Linux

root@ubuntu:~# more /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM
UUID=bdd5e06b-afdb-4088-aaa3-64e42ae399dd /mnt/usb1 vfat  defaults 0 0

---

### Post by FreezWay on 2010-01-10
what does "sudo dmesg" give you?

---

