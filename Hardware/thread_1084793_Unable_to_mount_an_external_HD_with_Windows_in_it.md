---
title: "Unable to mount an external HD with Windows in it"
date: 2009-03-02
forum: Hardware
---

### Post by dr_cerebro on 2009-03-02
I have an external HD with Windows installed on it, I removed from another computer when its motherboard failed.

It has some important information I want to recover.

When I try to mount it (in LinuxMint Felicia), it displays a message than it is unable to mount, if I have windows try to secure remove the device, if not from command line try:sudo mount -t ntfs-3g/dev/sdb1/media/disk -o force, I had no results.  Windows does not even manage to work the controller for that USB device (the external HD).  And GNU/Linux just display this:

```
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

```

My fdisk -l output is:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2af52af4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650        7667      144585    b  W95 FAT32
/dev/sda3            7668       19457    94703175    5  Extended
/dev/sda5            7668        7876     1678761   83  Linux
/dev/sda6            7877       19080    89996098+  83  Linux
/dev/sda7           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b4c0b4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS

```

Any ideas how to fix this?

---

### Post by taurus on 2009-03-02
There should be some space in there.

```
sudo mkdir /media/disk
sudo mount -t ntfs-3g   /dev/sdb1   /media/disk -o force

```
Didn't we already go through this before?

---

### Post by dr_cerebro on 2009-03-02
Hi, thank you for your answer.

It worked.

I saw your answer in this thread:

[HTML]http://ubuntuforums.org/archive/index.php/t-705762.html[/HTML]

but I thought the problem was slightly different, I didn't wanted to mess with the file system without previously ask.

Thank you very much my friend.

---

### Post by dr_cerebro on 2009-03-02
One more question:

I have three other HD with the same problem (that is one of the reasons I changed to GNU/Linux)... Should I follow the same steps ?

---

### Post by taurus on 2009-03-02
You need to mount them to different mount points so you need to create those mount points first.

I assume they are all ntfs filesystems and you cannot mount them without the force option.

---

