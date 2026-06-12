---
title: "I have a meme stick that won't mount"
date: 2008-07-23
forum: Hardware
---

### Post by Alaxandar on 2008-07-23
OK I ave a mem stick that is formatted as a fat drive. But when I plug it in I get a message that says can't mount usb device.So are there any codes that I could try. Thnks

---

### Post by phidia on 2008-07-23
After you have the drive plugged in you could open a terminal and enter this > dmesg | tail & > sudo fdisk -l

Post the results here.

---

### Post by Alaxandar on 2008-07-23
alexander@alexander-desktop:~$ dmesg | tail
[   98.079920] Bluetooth: HCI socket layer initialized
[   98.141787] Bluetooth: L2CAP ver 2.9
[   98.141796] Bluetooth: L2CAP socket layer initialized
[   98.228442] Bluetooth: RFCOMM socket layer initialized
[   98.228468] Bluetooth: RFCOMM TTY layer initialized
[   98.228471] Bluetooth: RFCOMM ver 1.8
[  102.070561] NET: Registered protocol family 17
[  105.746543] NET: Registered protocol family 10
[  105.747367] lo: Disabled Privacy Extensions
[  116.669200] eth0: no IPv6 routers present
alexander@alexander-desktop:~$ 


alexander@alexander-desktop:~$ sudo fdisk -l 
[sudo] password for alexander: 
Sorry, try again.
[sudo] password for alexander: 

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97979797

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4866     1502077+   5  Extended
/dev/sda5            4680        4866     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9b3be6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4998    40146403+   7  HPFS/NTFS

Disk /dev/sdc: 259 MB, 259522560 bytes
8 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 496 * 512 = 253952 bytes
Disk identifier: 0xffffffff

Disk /dev/sdc doesn't contain a valid partition table
alexander@alexander-desktop:~$

---

### Post by phidia on 2008-07-23
It looks like this > Disk /dev/sdc: 259 MB, 259522560 bytes is your usb device and this "Disk /dev/sdc doesn't contain a valid partition table" is the reason you can't mount it. 
Do you think you have files/data on that disk? If you just formatted it you need to create a partition to store data. You can use gparted or from a terminal cfdisk to do that. If you need more info on partitioning check [this]("https://help.ubuntu.com/community/DrivesAndPartitions") out.

---

### Post by Alaxandar on 2008-07-23
it is  valid partition is there a way to get to the files without formating it

---

### Post by phidia on 2008-07-23
Ok, try this: create a mount point > sudo mkdir /mnt/mythumbdrive *call it whatever you want "/mnt" needs to be there-don't change that.
Now do this (all of the quoted stuff is done in terminal) > sudo mount -t vfat /dev/sdc /mnt/mythumbdrive Hope that works-if it doesn't I don't know.

---

### Post by Alaxandar on 2008-07-23
I tried both of those and I got this

alexander@alexander-desktop:~$ sudo mkdir /mnt/mythumbdrive 
[sudo] password for alexander: 
alexander@alexander-desktop:~$ sudo mount -t vfat /dev/sdc /mnt/mythumbdrive 
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

alexander@alexander-desktop:~$

---

### Post by phidia on 2008-07-23
From man mount: >  -t vfstype
              The  argument following the -t is used to indicate the file sys&#8208;
              tem type.  The file system types which are  currently  supported
              include:  adfs,  affs,  autofs,  coda, coherent, cramfs, devpts,
              efs, ext, ext2, ext3, hfs, hpfs,  iso9660,  jfs,  minix,  msdos,
              ncpfs,  nfs,  nfs4,  ntfs,  proc,  qnx4, ramfs, reiserfs, romfs,
              smbfs, sysv, tmpfs, udf, ufs, umsdos, usbfs, vfat,  xenix,  xfs,
              xiafs.   Note  that  coherent, sysv and xenix are equivalent and
              that xenix and coherent will be removed at  some  point  in  the
              future &#8212; use sysv instead. Since kernel version 2.1.21 the types
              ext and xiafs do not exist anymore. Earlier, usbfs was known  as
              usbdevfs.
  

You can try with any of those filesystem types or try "mount -a" instead of the -t and don't list a filesystem type.

---

### Post by Alaxandar on 2008-07-23
I replaced -t -a and i got this

alexander@alexander-desktop:~$ sudo mount -a vfat /dev/sdc /mnt/mythumbdrive 
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
alexander@alexander-desktop:~$

---

