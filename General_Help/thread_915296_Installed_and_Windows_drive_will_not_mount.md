---
title: "Installed and Windows drive will not mount"
date: 2008-09-09
forum: General Help
---

### Post by zoomy942 on 2008-09-09
I installed Ubuntu today on my workstation at work, and was planning on dual booting...  well, ubuntu messed up the windows boot loader and thats okay becasue i love ubuntu.

but when i go into the places menu, i dont have the windows drive as a place i can get my files from.

Here is my fdisk -l.  My windows drive is that top 80GB one

```
 zimmerman@Ubuntu-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c879c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb66bb107

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36241   291105801   83  Linux
/dev/sdb2           36242       36483     1943865   82  Linux swap / Solaris

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19930   160083968    7  HPFS/NTFS
zimmerman@Ubuntu-desktop:~$ 

```

i just need a few files off of it.  i read around in the forums but i didnt find anything that was specific to me.

---

### Post by zoomy942 on 2008-09-09
Tried making a few shortcuts and using

```
 sudo mount -t ntfs /dev/sda1 /media/windows

```

but to no avail

---

### Post by devosion on 2008-09-09
Does it give you an error message when you run that line?

Also try mounting without the -t and ntfs options.

---

### Post by zoomy942 on 2008-09-10
i tried that and got some errors.

i also redid the -t ntfs one so you could see what it says.

(i also repasted the earlier stuff so its a long flow of information instead of reading one set of code then another.

```
 zimmerman@Ubuntu-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c879c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb66bb107

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36241   291105801   83  Linux
/dev/sdb2           36242       36483     1943865   82  Linux swap / Solaris

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19930   160083968    7  HPFS/NTFS
zimmerman@Ubuntu-desktop:~$ 
zimmerman@Ubuntu-desktop:~$ sudo ntfsfix /dev/sda1
sudo: ntfsfix: command not found
zimmerman@Ubuntu-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c879c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb66bb107

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36241   291105801   83  Linux
/dev/sdb2           36242       36483     1943865   82  Linux swap / Solaris

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19930   160083968    7  HPFS/NTFS
zimmerman@Ubuntu-desktop:~$ sudo mount /dev/sda /media/windows
[sudo] password for zimmerman: 
mount: you must specify the filesystem type
zimmerman@Ubuntu-desktop:~$ sudo mount hpfs/ ntfs /dev/sda /media/windows
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
zimmerman@Ubuntu-desktop:~$ sudo mount hpfs/ntfs /dev/sda /media/windows
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
zimmerman@Ubuntu-desktop:~$ sudo mount -t hpfs/ntfs /dev/sda /media/windows
mount: unknown filesystem type 'hpfs/ntfs'
zimmerman@Ubuntu-desktop:~$ sudo mount -t ntfs /dev/sda /media/windows
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
zimmerman@Ubuntu-desktop:~$ 

```

---

### Post by zoomy942 on 2008-09-10
So i did some reading and got this.

```
 root@Ubuntu-desktop:~# mount -f /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
root@Ubuntu-desktop:~# mount -i /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
root@Ubuntu-desktop:~# 

```

---

### Post by zoomy942 on 2008-09-10
maybe i will just take the drive out and put it in another machine and get what i need.

but if i do that GRUB will get mad becasue the device list changed.

---

### Post by WRDN on 2008-09-10
When you tried to mount the disk in /media/windows, had you already created the folder in /media?

If not, first type:

```
sudo mkdir /media/windows
```

Then:

```
sudo mount -t ntfs /dev/sda1 /media/windows
```

If the folder is not created, then the latter of the 2 commands cannot find the mount point.

---

### Post by zoomy942 on 2008-09-10
> **WRDN said:**
> When you tried to mount the disk in /media/windows, had you already created the folder in /media?

If not, first type:

```
sudo mkdir /media/windows
```

Then:

```
sudo mount -t ntfs /dev/sda1 /media/windows
```

If the folder is not created, then the latter of the 2 commands cannot find the mount point.

here is what i got from that

```
 zimmerman@Ubuntu-desktop:~$ sudo mkdir /media/vista
[sudo] password for zimmerman: 
zimmerman@Ubuntu-desktop:~$ sudo mount -t ntfs /dev/sda1 /media/vista
Unexpected clusters per mft record (-126).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
zimmerman@Ubuntu-desktop:~$ 



```

---

