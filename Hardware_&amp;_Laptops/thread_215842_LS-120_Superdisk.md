---
title: "LS-120 Superdisk"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by TWFJR on 2006-07-14
My Bios does not support the LS-120. I installed the LS-120 into an external enclosure converting the LS-120 for usb. Hoping that hotplugging would pic it up. The "Disk Manager" recongnises the LS-120 as /dev/sdg. 

dmeg gives this readout: 
[17183808.084000] Additional sense: Cannot read medium - unknown format

fdisk -l gives this readout:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1306 10490413+ 83 Linux
/dev/sda2 1307 2612 10490445 83 Linux
/dev/sda3 2613 48641 369727942+ fd Linux raid autodetect

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 1 1306 10490413+ 82 Linux swap / Solaris
/dev/sdb2 1307 2612 10490445 c W95 FAT32 (LBA)
/dev/sdb3 2613 48641 369727942+ fd Linux raid autodetect

Disk /dev/md0: 757.2 GB, 757202681856 bytes
2 heads, 4 sectors/track, 184863936 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

tom@ubuntu:~$ sudo mount

/dev/sda2 on / type reiserfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/sda1 on /boot type reiserfs (rw,notail)
/dev/sdb2 on /windows type vfat (rw)

What is the issue here that needs to be resolved for me to read my superdisks? Pics are stored on the disks from Panasonic PalmCam. I have connected this Cam to USB and I've been able to copy and save the pics. But the LS-120 has not worked.
Using Dapper 6.06

I have added this line to, /etc/fstab:

/dev/sdg /media/floppy vfat rw,noauto,user,sync 0 0

I also added this line to, /etc/mtab:

/dev/sdg /media/floppy vfat rw,noauto,user,sync 0 0

I think that somehow this does not address hotplugging with USB. 

Do I need to do a mtab symlink:
ln -sf /proc/mounts /etc/mtab?

Made a floppy directory in /media.
Again, I don't think that addresses hotplugging. I have not found a usb directory. Do I need to create a USB dir?

tom@ubuntu:/etc$ mount
/dev/sda2 on / type reiserfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/sda1 on /boot type reiserfs (rw,notail)
/dev/sdb2 on /windows type vfat (rw)
/dev/sdg on /media/floppy type vfat (rw,noauto,user,sync)
tom@ubuntu:/etc$

 I can't mount an LS-120 disk

the syntax for mounting a windows-formatted (or new) LS-120 disk is

mount -t vfat /dev/hdc /mnt/floppy

where hdc is the device your drive is found as, and /mnt/floppy is where you normally mount ls120 disks. Note that superdisks use the entire device by default and not a partition (unlike Zip drives above).

---

### Post by TWFJR on 2006-07-17
I can't mount an LS-120 disk

the syntax for mounting a windows-formatted (or new) LS-120 disk is

mount -t vfat /dev/hdc /mnt/floppy

where hdc is the device your drive is found as, and /mnt/floppy is where you normally mount ls120 disks. Note that superdisks use the entire device by default and not a partition (unlike Zip drives above).


Doesn't seem as if anyone is interested in tackling this problem I have.  Give that my BIOS does not support the LS-120 am I just wasting my time trying to find away for a USB connection to work?  Given the information above, can anyone make suggestions?  The above info came off of the internet.

tom@ubuntu:~/HomeDirectories$ sudo mount -t vfat /dev/sdg /media/floppy
Password:
mount: /dev/sdg: can't read superblock
tom@ubuntu:~/HomeDirectories$ ls /dev/sdg -la
brw-rw---- 1 root plugdev 8, 96 2006-07-14 11:43 /dev/sdg

---

