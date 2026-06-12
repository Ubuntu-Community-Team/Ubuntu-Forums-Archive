---
title: "Problems mounting harddrives"
date: 2008-09-10
forum: Hardware
---

### Post by Iwneferi on 2008-09-10
I recently installed ubuntu 8.04 on my desktop. The system recognizes my harddrives, but says it cannot mount them. When I try to mount them from the "places" menu, I receive the error message:

Unable to mount the volume "Library"

>
Failed to read last sector (321653366): Invalid argument Perhaps the volume is a RAID/LDM but it wasn't set up yet, or the wrong device was used, or the partition table is incorrect. Failed to mount '/dev/sdc1': Invalid argument The device '/dev/sdc1' doesn't have a valid NTFS.

I'm really not sure what to do next. But I'm pretty good at following instructions. Especially if I am given to understand what I am trying to do.

If it's of help to know, when I type the command "sudo fdisk -l" I receive the response:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6f4f6f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9587    77007546   83  Linux
/dev/sda2            9588        9964     3028252+   5  Extended
/dev/sda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e827e82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2089    16778241    7  HPFS/NTFS

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e827e82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2089    16778241    7  HPFS/NTFS

Disk /dev/sdd: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         969     1953439+   6  FAT16

(I have three harddrives, one CDRom, and a flash drive plugged in at the moment.)

Thanks in advance for your help.

---

### Post by Iwneferi on 2008-09-10
If this helps, when I type the command "gedit /etc/fstab" I get the response:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=487eecb5-edc7-412d-ad2e-a66cbb51719b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b3b2aab8-676a-460a-947f-6c3df60d4324 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Paul41 on 2008-09-10
It looks like your sdc1 partition is NTFS. I have mounted FAT32 but never NTFS so I don't know if this will work but try:

```
sudo mount -t ntfs /dev/sdc1 /your/mount/location
```

where /your/mount/location is where ever you want the drive to be mounted.

---

### Post by Iwneferi on 2008-09-11
> **Paul41 said:**
> It looks like your sdc1 partition is NTFS. I have mounted FAT32 but never NTFS so I don't know if this will work but try:

```
sudo mount -t ntfs /dev/sdc1 /your/mount/location
```

where /your/mount/location is where ever you want the drive to be mounted.

I'm sorry, I don't understand. What do you mean by where I want the drive to be mounted? Do I have a choice??

---

### Post by Paul41 on 2008-09-11
> **Iwneferi said:**
> I'm sorry, I don't understand. What do you mean by where I want the drive to be mounted? Do I have a choice??

In Linux you don't have a C, D, E... drive like in Windows. You mount your drives into any directory on the file system. so you could mount it in /mnt/ntfs, or ~/myfolder (which would mount it in a myfolder directory in your home drive). This way you can mount it anywhere that works for you. just create a empty directory to mount it in.

So if you want to mount it in a directory called myfolder on your home drive it would be:

```
sudo mount -t ntfs /dev/sdc1 ~/myfolder
```

---

### Post by Iwneferi on 2008-09-11
I tried to mount it to /computer.

This is the response I received:

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


I'm not quite sure what to make of it. Too much technical speach for me.

---

### Post by Paul41 on 2008-09-11
Do you have a /computer directory?  If not create it before trying to mount there.

---

### Post by freakie on 2008-09-11
may be your path doesn't exit.
try this command

sudo su
cd /mnt
mkdir win
mount -t ntfs-3g /dev/sdc1 /mnt/win
cd /mnt/win
ls

make sure to install ntfs-3g
apt-get install ntfs-3g
normally default ubuntu already had ntfs-3g

after issue ls cmd if u can see ur file list means success. i don't know this might help u or not. i just trying to help.

---

### Post by Iwneferi on 2008-09-12
> **Paul41 said:**
> Do you have a /computer directory?  If not create it before trying to mount there.

This is the directory my drives currently show up in. When I try to view files in any of my drives "except the Flash Drive" linux tells me that my drives cannot be mounted.


> **freakie said:**
> may be your path doesn't exit.
try this command

sudo su
cd /mnt
mkdir win
mount -t ntfs-3g /dev/sdc1 /mnt/win
cd /mnt/win
ls

make sure to install ntfs-3g
apt-get install ntfs-3g
normally default ubuntu already had ntfs-3g

Your instructions seemed to be working fine until I entered the command "mount -t ntfs-3g /dev/sdc1 /mnt/win". I received the same response as I have before when trying to mount my drives:


Failed to read last sector (321653366): Invalid argument
Perhaps the volume is a RAID/LDM but it wasn't setup yet, or the
wrong device was used, or the partition table is incorrect.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
root@Hathor:/mnt# 


When I entered the command "apt-get install ntfs-3g" in a new terminal, I received the response:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Paul41 on 2008-09-12
> This is the directory my drives currently show up in. When I try to view files in any of my drives "except the Flash Drive" linux tells me that my drives cannot be mounted.

I don't have a computer right now where I can run the desktop version of Ubuntu so I am going off of memory but if I remember correctly the /Computer you are talking about is a place that displays all your mounted drives but is not where they are actually mounted. You can see where the drives are mounted by running the following in the command line:
```
df
```

> When I entered the command "apt-get install ntfs-3g" in a new terminal, I received the response:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

you need to run apt-get as root so:

```
sudo apt-get install ntfs-3g
```

---

### Post by Iwneferi on 2008-09-13
OK, the command "df" brought up the response:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             76400416   3043740  69506300   5% /
varrun                  517688       104    517584   1% /var/run
varlock                 517688         0    517688   0% /var/lock
udev                    517688        76    517612   1% /dev
devshm                  517688        48    517640   1% /dev/shm
lrm                     517688     39760    477928   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      76400416   3043740  69506300   5% /home/iwneferi/.gvfs
/dev/sdd1              1953184    142624   1810560   8% /media/disk


This makes little sense to me, but I'm hoping you can help me sort it out.

And thanks for fixing the other command line for me. It simply responds that ntfs-3g is already the newest version, so I'm assuming I don't have to art that out any further...

---

### Post by Paul41 on 2008-09-13
> OK, the command "df" brought up the response:

Filesystem 1K-blocks Used Available Use% Mounted on
/dev/sda1 76400416 3043740 69506300 5% /
varrun 517688 104 517584 1% /var/run
varlock 517688 0 517688 0% /var/lock
udev 517688 76 517612 1% /dev
devshm 517688 48 517640 1% /dev/shm
lrm 517688 39760 477928 8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon 76400416 3043740 69506300 5% /home/iwneferi/.gvfs
/dev/sdd1 1953184 142624 1810560 8% /media/disk


This makes little sense to me, but I'm hoping you can help me sort it out.

This is showing you where your drives are mounted. If you look at the "filesystem" part that is the actual drive and the "Mounted on" part is the directory the drive is mounted in. So for example your /dev/sda1 is mounted in the root directory (/ is the root) and your /dev/sdd1 is mounted in /media/disk. So the /Computer you were talking about earlier is just showing you all mounted drives, but now where they are mounted.

> And thanks for fixing the other command line for me. It simply responds that ntfs-3g is already the newest version, so I'm assuming I don't have to art that out any further...

That's correct...you already had ntfs-3g so you don't need to do any more with this.

---

### Post by Paul41 on 2008-09-13
Posted a guide link but removed it because I realized it was for a older version.

---

### Post by IntuitiveNipple on 2008-09-13
Open a terminal (Applications > Accessories > Terminal), run these commands and copy the results to a reply here:
```

udevinfo --query=all --name=sdb1

udevinfo --query=all --name=sdc1

```
You should expect to see something similar to this output:
```

udevinfo --query=all --name=sda2

P: /block/sda/sda2
N: sda2
S: disk/by-id/scsi-1ATA_FUJITSU_MHV2200BT_NY06T6B26ANA-part2
S: disk/by-id/ata-FUJITSU_MHV2200BT_NY06T6B26ANA-part2
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2
S: disk/by-uuid/E6E08581E0855927
S: disk/by-label/Vista
E: DEVTYPE=partition
E: ID_VENDOR=ATA
E: ID_MODEL=FUJITSU_MHV2200B
E: ID_REVISION=0000
E: ID_SERIAL=1ATA_FUJITSU_MHV2200BT_NY06T6B26ANA
E: ID_SERIAL_SHORT=ATA_FUJITSU_MHV2200BT_NY06T6B26ANA
E: ID_TYPE=disk
E: ID_BUS=scsi
E: ID_ATA_COMPAT=FUJITSU_MHV2200BT_NY06T6B26ANA
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_FS_USAGE=filesystem
E: ID_FS_TYPE=ntfs
E: ID_FS_VERSION=3.1
E: ID_FS_UUID=E6E08581E0855927
E: ID_FS_UUID_ENC=E6E08581E0855927
E: ID_FS_LABEL=Vista
E: ID_FS_LABEL_ENC=Vista
E: ID_FS_LABEL_SAFE=Vista

```

---

### Post by Iwneferi on 2008-09-14
udevinfo --query=all --name=sdb1


P: /block/sdb/sdb1
N: sdb1
S: disk/by-id/scsi-1ATA_HDS724040KLAT80_KRFA06RAH9UW6D-part1
S: disk/by-id/ata-HDS724040KLAT80_KRFA06RAH9UW6D-part1
S: disk/by-path/pci-0000:00:06.0-scsi-1:0:0:0-part1
S: disk/by-uuid/36B0865EB0862509
S: disk/by-label/Entertainment
E: DEVTYPE=partition
E: ID_VENDOR=ATA
E: ID_MODEL=HDS724040KLAT80
E: ID_REVISION=KFAO
E: ID_SERIAL=1ATA_HDS724040KLAT80_KRFA06RAH9UW6D
E: ID_SERIAL_SHORT=ATA_HDS724040KLAT80_KRFA06RAH9UW6D
E: ID_TYPE=disk
E: ID_BUS=scsi
E: ID_ATA_COMPAT=HDS724040KLAT80_KRFA06RAH9UW6D
E: ID_PATH=pci-0000:00:06.0-scsi-1:0:0:0
E: ID_FS_USAGE=filesystem
E: ID_FS_TYPE=ntfs
E: ID_FS_VERSION=3.1
E: ID_FS_UUID=36B0865EB0862509
E: ID_FS_UUID_ENC=36B0865EB0862509
E: ID_FS_LABEL=Entertainment
E: ID_FS_LABEL_ENC=Entertainment
E: ID_FS_LABEL_SAFE=Entertainment




udevinfo --query=all --name=sdc1


P: /block/sdc/sdc1
N: sdc1
S: disk/by-id/scsi-1ATA_HDS722516VLAT20_VN64LRCDF8Z6BE-part1
S: disk/by-id/ata-HDS722516VLAT20_VN64LRCDF8Z6BE-part1
S: disk/by-path/pci-0000:00:06.0-scsi-1:0:1:0-part1
S: disk/by-uuid/F8FCA9BBFCA97492
S: disk/by-label/The\x20Library
E: DEVTYPE=partition
E: ID_VENDOR=ATA
E: ID_MODEL=HDS722516VLAT20
E: ID_REVISION=V34O
E: ID_SERIAL=1ATA_HDS722516VLAT20_VN64LRCDF8Z6BE
E: ID_SERIAL_SHORT=ATA_HDS722516VLAT20_VN64LRCDF8Z6BE
E: ID_TYPE=disk
E: ID_BUS=scsi
E: ID_ATA_COMPAT=HDS722516VLAT20_VN64LRCDF8Z6BE
E: ID_PATH=pci-0000:00:06.0-scsi-1:0:1:0
E: ID_FS_USAGE=filesystem
E: ID_FS_TYPE=ntfs
E: ID_FS_VERSION=3.1
E: ID_FS_UUID=F8FCA9BBFCA97492
E: ID_FS_UUID_ENC=F8FCA9BBFCA97492
E: ID_FS_LABEL=The Library
E: ID_FS_LABEL_ENC=The\x20Library
E: ID_FS_LABEL_SAFE=The_Library

---

