---
title: "Unable to mount NTFS partition - /dev/hda* is missing"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by Neutraleyes on 2005-04-05
Hi,

Firstly, my apologies if this is a common issue. I have been searching through threads for the past hour or so trying to get it fixed and have had no luck.

I have a Windows HDD (hda) and an Ubuntu HDD (hdd) and am trying to mount the ntfs partitions on hda. 

fdisk -l sees the partitions:
> Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2490    20000893+  42  SFS
/dev/hda2            2491       24792   179140815   42  SFS

but neither /dev/hda1 nor /dev/hda2 exists, so I can't get them mounted:
> neut@neutnix:~$ sudo mount -a
mount: special device /dev/hda2 does not exist
neut@neutnix:~$ ls /dev/hd*
/dev/hda  /dev/hdc  /dev/hdd  /dev/hdd1  /dev/hdd2  /dev/hdd5
neut@neutnix:~$

Here is my /etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2       /media/storage  ntfs    umask=0222 0 0

and here is what is currently mounted:
> /dev/hdd1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

Hope this is enough information - I am really liking Ubuntu and it'd be great if I could access my stuff on the other partition. Thanks in advance!

---

### Post by maqi on 2005-04-05
I haven't tried mounting ntfs drives in fstab in ubuntu, but in debian I use the following options in fstab:

[b]/dev/hdxx /mnt/xx ntfs  ro,defaults,umask=022  0      0
[/b]
I will add that I have no problem manually mounting my ntfs drives in ubuntu if I need them. A simple:

[b]$ sudo mkdir /mnt/point
$ sudo mount /dev/hdx /mnt/point
[/b]
works just fine. Give it a try.

Also, try the following to check if the ntfs module is loading properly:

[b]$ sudo modprobe ntfs
$ lsmod | grep ntfs[/b]

You should get something like the following:

**ntfs                  112624  0**

Finally, and not likely considering fdisk, is your windows drive a sata drive? If so the device name will be /dev/sdxx.

Good luck :)

maqi

---

### Post by Randar on 2005-10-14
I have a similar issue. I have Windows 2000 and Ubuntu 5.04 x86_64 on the same hard drive. when I'm using ubuntu, The Windows partition is mounted as /media/hdd1, but it is inaccessible. It says
> You do not have the permissions necessary to view the contents of "hdd1".
when I try to open it, so I have no clue what to do.

Also it shows the owner as "root"

Thanks in advance. ;)

EDIT: Has anyone seen this? Should I list this as a topic?

---

### Post by kb0odu on 2005-11-21
1.  Log in as root and create a directory in media for your Windows mount point.  In my case, I called it **Windows**.  Make note of this.  You'll be using it in step 2.

2.  Log in as root and add an entry to /etc/fstab similar to the following (NOTE: You need to know which partition windows is installed on!  In my case, Windows XP is installed on hda2.  This is only because I'm using my work laptop.)

[B]/dev/hda2          /media/windows          ntfs         nosuid,nodev        0      0
[/B]

3.  As a user, enter the command:
**    mount /media/windows**

You may have to play with permissions to get this to work correctly.

YMMV...

Tim

---

### Post by tOpEzz on 2005-11-22
hello, i'm a new ubuntu user... can anyone help me or gimme some link that showing or guide regarding to mount partition?? thanks

---

### Post by aysiu on 2005-11-22
[QUOTE=tOpEzz]hello, i'm a new ubuntu user... can anyone help me or gimme some link that showing or guide regarding to mount partition?? thanks[/QUOTE] [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

