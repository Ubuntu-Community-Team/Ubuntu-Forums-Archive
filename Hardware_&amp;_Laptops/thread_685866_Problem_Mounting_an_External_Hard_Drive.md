---
title: "Problem Mounting an External Hard Drive"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by Qharos on 2008-02-02
Running Gutsy Gibbon, rather fresh install. While using the Live CD, I was able to plug-in and access my external hard drive, and see the contents. Now I can't. At one point the cord got knocked loose, and the system mentioned an unsafe removal. Now when I try to open it (only one partition has issues):


```
Cannot mount volume.

Unable to mount the volume 'WD Passport'.

Details
$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1'; Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sdb/1 /media/WD Passport -o force     Or add the option to the relevant row in the /etc/fstab file: /dev/sdb1 /media/WD Passport ntfs-3g defaults,force 0 0
```

So I don't have easy access to a Windows box (if that's the best solution, I can be patient and do that, but for now, is one of these just as safe?)

I prefixed "sudo" in front since it said "only root can do that":

```
taylor@home:~/Desktop$ sudo mount -t ntfs-3g /dev/sdb1 /media/WD Passport -o force
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

This is what a **sudo fdisk -l** returns:

```
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9172    73674058+  83  Linux
/dev/sda2            9173        9546     3004155    5  Extended
/dev/sda5            9173        9546     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              20       16907   135652860    7  HPFS/NTFS
/dev/sdb2   *       16908       19330    19462747+  83  Linux
/dev/sdb3           19331       19457     1020127+  82  Linux swap / Solaris
```

Long story short on that, I tried to install Linux onto the eHD... I could still see the WD Passport section after I gave up that and installed this freshly onto the main HD, though. /dev/sdb1 is WD Passport.

When I try a manual umount, it says it's not mounted.

I couldn't easily find a thread that pertained to this specific issue. Suffice to say, I'm at a loss. The drive has all my backups and important files on it, too, so I'd really like to avoid losing that data. Thanks muchly.

---

### Post by jan quark on 2008-02-03
try the following

```
sudo mkdir /media/data
```
```

sudo mount /dev/sdb1 /media/data -t ntfs -o nls=utf8,umask=007
```

]

---

### Post by Qharos on 2008-02-04
> **jan quark said:**
> try the following

```
sudo mkdir /media/data
```
```

sudo mount /dev/sdb1 /media/data -t ntfs -o nls=utf8,umask=007
```

]

Tried that, here's the results:

```
sudo mount /dev/sdb1 /media/data -t ntfs -o nls=utf8,umask=007
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/data -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/data ntfs-3g defaults,force 0 0

```

No luck. :(  Will connecting it to a Windows machine then removing it that way really resolve this? Kind of troublesome it seems to be the only feasible way.

---

### Post by Qharos on 2008-02-04
I had luck googling that error, though.

[http://bbs.archlinux.org/viewtopic.php?pid=317384](http://bbs.archlinux.org/viewtopic.php?pid=317384)


Solution Steps:
1) sudo chmod u+s /bin/ntfs-3g
2) mount -t ntfs-3g /dev/sdb1 /media/data -o force


Data seems intact. Thank goodness.

---

### Post by vahnx on 2008-02-04
Every time my external doesn't mount, I run this and it works:
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
Now you might have to mkdir /dev/sdb1 or /media/sdb1

The cause is probably like mine, I always unplug my USB devices without manually unmounting it.

---

