---
title: "Can't mount hardware..."
date: 2011-07-28
forum: Hardware
---

### Post by silveringking on 2011-07-28
Hi, my Ubuntu doesnt recognize one external disk that I have:

Here is the log

> carlos@carlos:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007419c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6502    52227283+  17  Hidden HPFS/NTFS
/dev/sda2   *        6503       13004    52227315   83  Linux
/dev/sda3           13005       13145     1132582+  82  Linux swap / Solaris
/dev/sda4           13146       19457    50701109+   f  W95 Ext'd (LBA)
/dev/sda5           13146       19457    50701108+   7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e96bb

   Device Boot      Start         End      Blocks   Id  System
carlos@carlos:~$ sudo mount /dev/sdb
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
carlos@carlos:~$ sudo mount /dev/sda1 /media/Elements
fuse: failed to access mountpoint /media/Elements: Ficheiro ou directoria inexistente
carlos@carlos:~$ sudo mount /dev/sda1 /media
carlos@carlos:~$ sudo mount /dev/sdb /media
mount: you must specify the filesystem type
carlos@carlos:~$ sudo mount nfts  /dev/sdb /media
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
carlos@carlos:~$ mount device
mount: can't find device in /etc/fstab or /etc/mtab
carlos@carlos:~$  mount -a [-t|-O] /media
mount: only root can do that
-O]: comando não encontrado
carlos@carlos:~$ sudo mount -a [-t|-O] /media
mount: can't find [-t in /etc/fstab or /etc/mtab
-O]: comando não encontrado
carlos@carlos:~$ 


What can I do?

---

### Post by SlugSlug on 2011-07-28
is the drive formatted? It's not showing a partition

try use gnome partition tool to see whats going on

sudo apt-get install gparted

---

