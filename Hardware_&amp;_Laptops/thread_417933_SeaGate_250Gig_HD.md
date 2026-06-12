---
title: "SeaGate 250Gig HD"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by zombiepunkcaptain on 2007-04-22
Just switched over from WinXP to Feisty - I was under the impression that I would still retain the ability to "Plug n' Play" my SeaGate External HD, however it doesnt appear to be working.

I have tried looking through the file system, to be honest I'm not too sure where to look, but I think there may be compatibility issues because my 4Gig Flash Card appeared on the desktop immediately.


I'm sorry I haven't provided you with much information, I'm not yet sure what information you need.

All replies will be greatly appreciated.

---

### Post by taurus on 2007-04-22
How about the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Spartan.II.117 on 2007-04-22
have you tried looking in/media? also what filesystem is your drive (i assume it's ntfa since fat cant handle a drive that size)

---

### Post by zombiepunkcaptain on 2007-04-22
> **taurus said:**
> How about the output of this command from a terminal?

```
sudo fdisk -l
```

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9434    75778573+  83  Linux
/dev/sdb2            9435        9726     2345490   82  Linux swap / Solaris

Disk /dev/sdc: **250.0 GB**, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    c  W95 FAT32 (LBA)
```

The one in bold is my external Hard-Drive - and gorrammit, it appears it is in FAT32?

Where to now?

Thanks a lot for your quick replies.

---

### Post by taurus on 2007-04-22
From a terminal, do

```
sudo mkdir /media/windows
sudo mount -t vfat /dev/sdc1 /media/windows -o iocharset=utf8,umask=000
df -h
```

---

### Post by Spartan.II.117 on 2007-04-22
can you post the contents of your fstab file?

```
gedit /etc/fstab
```

EDIT: nevermind, i did not see the last post.

---

### Post by zombiepunkcaptain on 2007-04-22
> **taurus said:**
> From a terminal, do

```
sudo mkdir /media/windows
sudo mount -t vfat /dev/sdc1 /media/windows -o iocharset=utf8,umask=000
df -h
```

Taurus -

```
zombie@Zombie:~$ sudo mkdir /media/windows
Password:
mkdir: cannot create directory `/media/windows': File exists
zombie@Zombie:~$ sudo mount -t vfat /dev/sdc1 /media/windows -o iocharset=ut f8,umask=000
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
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
zombie@Zombie:~$
```

Spartan.II.117 -

I have to get "gedit" - will be back in a minute.

---

### Post by EnigMattic on 2007-04-22
Any ideas about my Seagate 320Gig?

*fdisk -l* output:
```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6996    56195338+  83  Linux
/dev/sda2            6997        7296     2409750    5  Extended
/dev/sda5            6997        7296     2409718+  82  Linux swap / Solaris

[B]Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA)[/B]

```

Contents of */etc/fstab*
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=268ef6c3-718a-44e8-b553-853af375e39d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e3a540cf-26b0-4ac9-964c-605ec853b6a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom       /media/cdrom1   udf,iso9660 user,noauto     0       0
```

Any ideas?
(btw, mounts with *sudo mount -t vfat /dev/sdb1 "/media/MATT'S_DISK" -o iocharset=utf8,umask=000*, though doesn't show up on desktop)

---

### Post by ElVirolo on 2007-04-22
Look at this : [https://bugs.launchpad.net/bugs/102097](https://bugs.launchpad.net/bugs/102097)

---

### Post by zombiepunkcaptain on 2007-04-22
> **EnigMattic said:**
> Any ideas about my Seagate 320Gig?

I think there is a recurring theme of Seagate HD's being shipped using the FAT32 File System, which appears to be Linux un-friendly.

Can anyone confirm or deny that?

Will a reformat in NTFS do the trick?

Will I be able to access files in both Linux and WinXP?

---

### Post by Spartan.II.117 on 2007-04-22
you'll have to install ntfs-config, first and enable mounting of external ntfs partitions as read/write, but it should work.

---

### Post by zombiepunkcaptain on 2007-04-22
> **Spartan.II.117 said:**
> you'll have to install ntfs-config, first and enable mounting of external ntfs partitions as read/write, but it should work.

From what little I can understand of the .txt output it seems to me that both EnigMatic and my HD are formatted in FAT32.

So to me that means that ntfs-config wouldn't do anything - as the HD are not in the same File System.


I don't know - I'm new to this. It's quite likely I am wrong.

What does everyone think?

---

### Post by Spartan.II.117 on 2007-04-22
> **zombiepunkcaptain said:**
> 
Will a reformat in NTFS do the trick?

i was responding to this

---

### Post by zombiepunkcaptain on 2007-04-22
Ok mate, ta.

Well I guess that's a job for the weekend. Thanks a lot for all your help.

---

