---
title: "partition mess up"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by ygong on 2007-01-02
I have redhat linux and windows xp installed in my IBM laptop and I decided to try ubuntu, so I installed ubuntu. After the installation, I wanted to delete the redhat linux, so I partitioned my hard disk and then got messed up, now I cannot enter the operating system. The computer gave error message when started grub. The gpart cannot recogonize my partition in the hard disk. But when I used the hard disk as a jump disk in windows system, I can see all the files. The partition magic cannot recognize the partition either. How can I re-install the grub and make the partition recognizable? Please help!

---

### Post by bronson on 2007-01-02
Boot with a liveCD, use cfdisk or gparted to fix your partition table (be VERY careful here).  Once you've got the partition set up, you can re-install Grub: [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by ygong on 2007-01-03
Thanks for the reply, could you please give me detailed instruction how to fix the partition?
Thanks

---

### Post by ygong on 2007-01-03
By the way, the message in boot up is as follows:
Loading grub, stage 1.5
Grub loading, please wait .....
Error 17

Thanks

---

### Post by ygong on 2007-01-03
the results of fdisk are
---------------------------------
Disk /dev/hda: 80.0GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
units=cylinders of 16065*512=8225280 bytes

Device       Boot    Start       End       Blocks            Id        System
/dev/hda1   *         1         5100    40965718+        7     HPFS/NTFS
/dev/hda2            5100    9729      37187609          f   W95 Ext'd (LBA)
Partition 2 does not end on cylinder bounday
/dev/ha5              5100   7257    17331741           83     Linux
/dev/hda6   *        7258   8852    12811806          83      Linux
/dev/hda7             8853    8924    578308+           82    Linux swap/Sloaris
/dev/hda8             8925   9186    2101648+         82     Linux swap/Solaris
/dev/hda9             9186   9729    4362088+          b       W95 FAT32
---------------------------------------
Results of cat /boot/grub/device.map:
(hd0) /dev/hda
------------------------------
menu.lst:
default 0
timeout 10
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,7)
kernel  /boot/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,7)
kernel  /boot/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,7)
kernel  /boot/memtest86+.bin
quiet
boot



Somebody please help me fix the partition

---

