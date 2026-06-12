---
title: "Install on USB Stick with 2 drives"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by weliwarmer on 2009-03-27
Hi,

I have had for years a 1Gig flash stick that boots Ubuntu 8.04.

My new stick has 2 drives (note drives not partitions) that appear as /dev/hdb and /dev/hbc

the /dev/hdb is a very small 2Meg
the /dev/hdc is 4Gig

The 8.10 USB installer put the new a bootable install on hdc as requested but the stick is not bootable.  I gather the bios is looking on hdb for the mbr and not finding one.  The 1Gig stick boots fine in the same PC.

I'm going to create an mbr and install grub on the small 2Meg drive (hdb) and then fiddle with grub until it boots using the kernel on hbc.  Do you think that will work or am I wasting my time?

Can anyone recommend a better method for fixing this stick?

Thanks,
Tim

integral 4GB

---

### Post by dandnsmith on 2009-03-27
You don't say what the originator of the usb stick is - could it be SanDisk?

There are some curiously set up usb sticks, which show this feature (I have a couple), usually associated with the ability to lock files or encrypt them.

If you don't worry too much, you could try removing any partition table, recreating one, add at least one partition and format it. This might 'fix' it, but I haven't seen anyone recommend it.

Later: I think that may not be a good thing to try, after all. I decided, while walking around, that I really cannot work out why it gets presented as two different letters, rather than as 2 partitions (eg sda1, sda2), so perhaps there is something special in the hardware to arrange it. It may never be possible to present it all as one drive.

---

### Post by weliwarmer on 2009-03-27
Hi Derek,

Thanks for the reply.  It's an integral 4GB.

I've deleted the partition table on both sdb and sdc (going old-skool when I called then hdb and hdc!) and recreated them.  Still two drives though and the first is not big enough for Linux.

Just going to try installing a new mbr and grub on the 2Meg drive/portion/thingy and see if I can get that to point to the second drive.  

If it was just two partitions and one partition table, I'd be a happy bunny!

Thanks again,
Tim

---

### Post by weliwarmer on 2009-03-27
Hummmm....

After 20 years of UNIX and I can't get a little usb stick to boot.  If anyone can help, I'd be grateful...

Here's the info:

```
# fdisk /dev/sdb

Command (m for help): p

Disk /dev/sdb: 2 MB, 2097152 bytes
1 heads, 4 sectors/track, 1024 cylinders
Units = cylinders of 4 * 512 = 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2        1024        2046   83  Linux

# fdisk /dev/sdc

Command (m for help): p

Disk /dev/sdc: 4001 MB, 4001366016 bytes
124 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         214      822615+   6  FAT16
/dev/sdc2             215        1016     3082888   83  Linux

```

sdb1 was built just with mke2fs and copying boot and some things from syslinux:

```
# ls -lR /media/disk/
/media/disk/:
total 13
drwxr-xr-x 3 root root  1024 2009-03-27 19:50 boot
drwx------ 2 root root 12288 2009-03-27 19:49 lost+found

/media/disk/boot:
total 1
drwxr-xr-x 2 root root 1024 2009-03-27 20:38 grub

/media/disk/boot/grub:
total 1582
-rw-r--r-- 1 root root      15 2009-03-27 19:54 device.map
-rw-r--r-- 1 root root   20068 2009-03-27 19:55 memdisk
-rw-r--r-- 1 root root    4267 2009-03-27 20:38 menu.lst
-r--r--r-- 1 root root 1474560 2009-03-27 19:56 sbm.bin
-rw-r--r-- 1 root root     512 2009-03-27 19:51 stage1
-rw-r--r-- 1 root root  108356 2009-03-27 19:51 stage2

/media/disk/lost+found:
total 0

```

The USB boot wizard in 8.10 created the /dev/sbc1 and /dev/sdc2

```
# ls -lR /media/live/
/media/live/:
total 8
drwx------ 3 tim root 4096 2009-03-26 22:29 boot
dr-x------ 2 tim root 4096 2008-10-29 23:24 casper

/media/live/boot:
total 4
drwx------ 2 tim root 4096 2009-03-26 22:29 syslinux

/media/live/boot/syslinux:
total 20
-r-x------ 1 tim root 13973 2009-03-26 22:29 ldlinux.sys
-rwx------ 1 tim root   146 2009-03-26 22:29 syslinux.cfg

/media/live/casper:
total 702112
-r-x------ 1 tim root     34764 2008-10-29 23:17 filesystem.manifest
-r-x------ 1 tim root     32672 2008-10-29 23:14 filesystem.manifest-desktop
-r-x------ 1 tim root 708198400 2008-10-29 23:21 filesystem.squashfs
-r-x------ 1 tim root   8448174 2008-10-29 23:17 initrd.gz
-r-x------ 1 tim root   2244272 2008-10-24 09:29 vmlinuz

```

Grub menu.lst looks like this:

```
title Floppy Test Image
kernel  /boot/grub/memdisk
initrd  /boot/grub/sbm.bin

title		Ubuntu
root		(hd2,0)
kernel		/casper/vmlinuz ro quiet
initrd		/casper/initrd.gz
quiet

```

Grub just reports file not found when booting Ubuntu.

Please help.

Tim

---

### Post by dandnsmith on 2009-03-30
The only sure-fire way I've found so far for booting usb sticks is to use [UnetBootin](http://unetbootin.sourceforge.net/) for creating a live distro, rather than a full install on the usb stick.
This puts a version of syslinux (or related thing), and uses it to create the bootloader at the start.

This may not be quite what you want.

Caveat - not all PCs will boot from a usb stick, and some are quite choosey about what methods they will allow a particular model of stick to use.

I'm only just moving into the full install on a stick.

---

