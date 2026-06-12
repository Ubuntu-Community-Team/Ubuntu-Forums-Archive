---
title: "Accident with External Hard Drive, is all hope lost ?"
date: 2011-04-23
forum: Hardware
---

### Post by skjebne on 2011-04-23
Well, I'm still baffled by my own stupidity.

I've had some problems with 11.04 Beta 2 on my desktop, namely it would very often drop connections, so I decided to revert back to 10.10. Since I wanted to have a separate /home partition now, I decided that, rather than moving it, I'd reformat the whole hard drive and create separate partitions for /boot, /, /swap and /home. Everything went quite nicely until I spotted an other drive with 320Gig free. My desktop has a 320Gig HDD so, this being the first time I managed my partitions manually, I figured it must be a copy of my hard drive and I didn't think more about it. 

GREAT MISTAKE !

It was actually my external HDD, a LaCie which also has 320Gig. So I went ahead with the installation, went downstairs to the birthday family party for my sister. When I came back up, it was ready to go. I rebooted, ran the update manager, installed my stuff and the additional drivers and rebooted again. My desktop now works perfectly again (I think I'll wait some time to install 11.04, so Canonical & the community can iron out some problems), which is great. But then I started looking for my external HDD to put all of my backup back on my desktop. THAT's when I realised it had been hooked to it the whole time. It didn't show on desktop. I thought, hum, strange. I went to the disk utility and that's when I started panicking. It now shows this : [http://img845.imageshack.us/f/screenshotmim.png/](http://img845.imageshack.us/f/screenshotmim.png/)


I tried mounting /dev/sdb but it won't allow me. (I just created a /media/external as recommanded on help.ubuntu)
This is what it returns when I do 
sudo mount -t vfat /dev/sdb /media/external
```

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```or when I do 
sudo mount -t ntfs-3g /dev/sdb /media/external
```

NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
skjebne@skjebne-X71SL:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/external
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory

ntfs-3g 2010.8.8 external FUSE 28 - Third Generation NTFS Driver
        Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org]("http://ntfs-3g.org/")
skjebne@skjebne-X71SL:~$ sudo mount /dev/sdb /media/external
mount: you must specify the filesystem type
skjebne@skjebne-X71SL:~$ sudo mount vfat /dev/sdb /media/external
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
```So I guess it's not NTFS

The first step for me would be to be able to mount it. And then, in a perfect world, be able to recover at least some parts of my data (I have the only known copies of "The Plan B" and its two sequels, the highly successful trilogy I filmed in school. So it's kindda emotional ...)

To be perfectly honest, I really don't remember if I checked the "format" box when I installed 10.10.

---

### Post by skjebne on 2011-04-24
Well. It was actually really easy to fix.

if you have the same problem as I did have, namely having a hard drive showing up as a 100% "free" in the disk utility but refusing to mount, just download testdisk.

```

sudo apt-get install testdisk 
```

then run it

```
sudo testdisk
```

If you're as lucky as I was, you'll be able to recover as much as ... all of your data ! :)
Just Navigate the disk and copy the files (by default, they're sent to your /home folder.

Now I know all "serious" Linux users already knew about that, but if it can help any newbie, then I did my part ;)

---

