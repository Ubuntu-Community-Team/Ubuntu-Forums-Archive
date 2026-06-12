---
title: "DVD-ROM mounting problems - HELP"
date: 2008-07-22
forum: Hardware
---

### Post by Inprogress on 2008-07-22
Hi.

Have weird problem. I'm a newbie to Linux and more so Xubuntu. Loads fine on my laptop, but my friend has this error message:

Failed to mount "DVD-R Disc".
mount: block device/dev/hda is write-protected, mounting read-only.
mount: wrong fs type, bad option, bad superblock on /dev/hda, missing codepage or helper program, or other error
In some cases useful info is found in syslog - try dmesg|tail or so.

Now funny part is, it loads the main repository DVD fine (Ubuntu 7.10) but not any of the rest. Xubuntu 8.04 i386. He has a Fujitsu Siemens Amilo Li 1718.

I'm new to Linux so if you need more info I will supply it if you tell me how to give it (refering to system data using the OS).

Thanks so much and hope you can help soon, would really like to get it working on his laptop, he gives up quickly.

---

### Post by Potatoj316 on 2008-07-22
Do you get this error when you put the CD in the cd drive or do you get it when you boot?

---

### Post by sisco311 on 2008-07-22
insert a cd.
open a terminal(Applications -> Accessories -> Terminal) and type:
```
dmesg | tail
``````
cat /etc/fstab
```and
```
lshw -C disk
```post the output.

---

### Post by Inprogress on 2008-07-23
Hi Sisco311. Thanks for the reply, you to Potatoj316. Here is the output of each line:

dmesg | tail
[ 251.502191] attempt to access beyond end of device
[ 251.502205] hda: rw=0, want=68, limit=4
[ 251.514087] attempt to access beyond end of device
[ 251.514098] hda: rw=0, want=1252, limit=4
[ 251.514110] attempt to access beyond end of device
[ 251.514115] hda: rw=0, want=1028, limit=4
[ 251.514120] UDF-fs: No partition found (1)
[ 251.542015] attempt to access beyond end of device
[ 251.542028] hda: rw=0, want=68, limit=4
[ 251.542052] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block

cat /etc/fstab
# /etc/fstab: static file system information
#
# <file system> <mount point>  <type> <options> <dump> <pass>
proc            /proc          proc   defaults   0      0
# /dev/sda1
UUID=c113f38d-b76e-46af-9ada-f26acc907289 /   ext3  relatime,errors=remount-ro 0    1
# /dev/sda5
UUID=20d055aa-9517-4231-b7b1-db0f046c1629 none   swap   sw    0  0
/dev/hda   /media/cdrom0  udf,iso9660 user,noauto,exec,utf8 0  0


lshw -C disk
WARNING: you should run this program as super-user
 *-cdrom
       product:Optairc DVD RW AD-7540A
       physical id: 0
       bus info:ide@0.0
       logical name: /dev/hda
       capacity: 2KiB (2048B)
       capabilites: packet

Hope this helps cause it took me some eyestrain and time to copy this down. If it is a stupid way, have a laugh on me!:lolflag:

---

### Post by Inprogress on 2008-07-25
Hi Potato. Xubuntu is installed and running. I insert the 1st DVD repository (1 of 5) and that gets loaded, but any of the rest gives me that message. I tried some other DVD's and CD's. I have no idea why it would load and read the first one but not the rest, or one DVD and not any other.

---

