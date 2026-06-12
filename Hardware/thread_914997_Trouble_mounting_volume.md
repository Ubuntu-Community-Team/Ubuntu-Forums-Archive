---
title: "Trouble mounting volume"
date: 2008-09-09
forum: Hardware
---

### Post by noah8956 on 2008-09-09
Hello,

1)  I'm running 8.04.1 on my eee pc 901.  I'm trying to mount the card reader and I get the following error message:

Cannot mount volume.  Must be superuser to use mount 

2)  I think this issue might be related (found on [http://www.ubuntu-eee.com/index.php5?title=EeePC_901):](http://www.ubuntu-eee.com/index.php5?title=EeePC_901):)

Remove the reference to the cdrom in the /etc/fstab, as you don't actually have a CD-ROM and it can conflict with mounting devices later: /dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

thanks,

noah

---

### Post by gforcing on 2008-09-09
The superuser part just means you have to put sudo before the command. Do you know where the card reader is located in /dev? A good way to find it is to use: ```
$ sudo fdisk -l
``` This will list the drives connected to your system.

Post the output of that and I'll try to help more specifically.

---

### Post by noah8956 on 2008-09-10
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by noah8956 on 2008-09-10
oops sorry, here is the correct response:

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8eb98eb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         462     3710983+  83  Linux
/dev/sda2             463         490      224910    5  Extended
/dev/sda5             463         490      224878+  82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000322bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1874    15052873+  83  Linux
/dev/sdb2            1875        1962      706860    5  Extended
/dev/sdb5            1875        1962      706828+  82  Linux swap / Solaris

Disk /dev/sdc: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         984     1983619+   6  FAT16

---

### Post by gforcing on 2008-09-10
First of all: I think the card reader might be /dev/sdc1. Do you have a 2GB card in the card reader? It would also be helpful if you could post your /etc/fstab to show how the drives are being mounted. 

The other reason I think /dev/sdc1 is your card reader is because it's using the FAT16 file system. But posting your /etc/fstab should clear that up.

---

### Post by noah8956 on 2008-09-10
please give the full command line, this is all very new to me.  thanks

---

### Post by noah8956 on 2008-09-10
...and yes i do have a 2 gb card in the reader

---

### Post by gforcing on 2008-09-10
To find out what's in fstab, use this command:

```
gedit /etc/fstab
```

Just copy paste that here.

---

### Post by wescb on 2008-09-12
I'm having the same issue on the same hardware. Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d020f592-c7ac-4fa9-ade2-459e061a7472 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5253fd49-108b-457a-9b2f-d8d25a8f546b none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by wescb on 2008-09-12
Doh.

I got it, I just commented out the line referring to the CD drive (sdc1) via the link above. [http://www.ubuntu-eee.com/index.php5?title=EeePC_901]("http://www.ubuntu-eee.com/index.php5?title=EeePC_901")

Sorry for the quasi-thread jack
Thanks,
Wes

---

### Post by paletti on 2008-12-03
Thanks, worked fine for me too!

Btw, for the noobs... commenting out means putting a # in front of the line, like this:

```
# /dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by dranoweb on 2010-06-17
something to try:

reboot, 

press f2 for bios menu

change os status to "complete" instead of "start"

---

