---
title: "Mounting second linux install in first &amp; vice-versa"
date: 2005-11-16
forum: General Help
---

### Post by ajgreeny on 2005-11-16
Can someone help me by showing how I can mount an installaton of breezy on a separate disk in my first installation of hoary?
Now I'm a bit more sure of how to use linux (and especially Ubuntu) I've added a triple boot of breezy with added KDE to my machine.  No problems there; its on hda2 and swap on hda5, with windows xp on hda1 and hoary on hdb1 with its swap on hdb5.
I would like to be able to read all the files on my home folder in hoary when using breezy, but so far have not been able to get it to work.  When I try to mount the partition for breezy in hoary I get the error:

mount: can't find /dev/hda2 in /etc/fstab or /etc/mtab
Please check that the disk is entered correctly.

I've tried adding the partition to fstab but must be doing it wrongly.  Also what do I need to add to mtab.

Great distro!  I'm totally hooked and seldom boot into windows these days;  just need it for the occasional bit of DTP for which I still love Serif Page Plus 10.

I hope someone can help.  This is a minor point but will make life a lot easier.

---

### Post by mlomker on 2005-11-17
Post the output of:

```

sudo fdisk -l
cat /etc/fstab

```

---

### Post by ajgreeny on 2005-11-17
OK mlomker,
Here's the output of the commands you asked for which I hope will help.


Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        8924    71681998+   7  HPFS/NTFS
/dev/hda2   *        8925       19741    86887552+  83  Linux
/dev/hda3           19742       19929     1510110    5  Extended
/dev/hda5           19742       19929     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4810    38636293+  83  Linux
/dev/hdb2            4811        4998     1510110    5  Extended
/dev/hdb5            4811        4998     1510078+  82  Linux swap / Solaris

andrew@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
andrew@ubuntu:~$                            

As I said, hdb1 has the original hoary installation, hda1 is windows xp, and now hda2 has breezy.

While you're answering questions, can you tell me what has happened to the icons for mounted hard disks on the kde desktop.  On hoary I get both the windows disk and the hoary disk icons showing, on breezy there's nothing.  In kcontrol I have set the desktop behaviour/device icons tab exactly the same, ie to show mounted hard disk volumes, but nothing shows.  What's missing please?

I still love Ubuntu and am learning fast, just not quite fast enough!

---

### Post by mlomker on 2005-11-17
You were trying to mount the Hoary partition when running Breezy.  From the looks of this output you were running Hoary when you did it.  I need to see the /etc/fstab from Breezy...

I'm not sure about the icons...I'll try enabling them and see what happens.

---

### Post by ajgreeny on 2005-11-18
Thanks for trying mlomker.

Here's the same output from breezy on hda2:-

Password:

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        8924    71681998+   7  HPFS/NTFS
/dev/hda2   *        8925       19741    86887552+  83  Linux
/dev/hda3           19742       19929     1510110    5  Extended
/dev/hda5           19742       19929     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4810    38636293+  83  Linux
/dev/hdb2            4811        4998     1510110    5  Extended
/dev/hdb5            4811        4998     1510078+  82  Linux swap / Solaris
andrew@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
andrew@ubuntu:~$                           

As far as I can make out there are no differences (not surprising) in the fdisk listing, and only minor ones in the fstab - for some reason the cdrom0 is not marked ro as it is in hoary, and the mounted ext3 partition is hda2 not hdb1.  As I said I would like to be able to see and copy across personal files from hoary to breezy and vice-versa, rather like I can from windows to breezy and to hoary at the moment.
It seems there is a way of doing just about anything you want in linux if you know how, or what file to change in some way, so I'm sure there must be a way to do this.
As for the disk icons on the kde desktop, there is another thread going which I discovered last night suggesting several people have had the same problem.  Perhaps a bug?  I'll keep looking.

Thanks again.  These forums are terrific for seeking answers to problems.  Better than any I've used before.  Just like Ubuntu really!

---

### Post by mlomker on 2005-11-18
First create a mount point for Hoary:

```

sudo mkdir /media/hoary

```

Then add the line to Breezy's /etc/fstab:

```

/dev/hdb1       /media/hoary   ext3    defaults  0  1

```

**sudo mount -a** should mount it to that directory.

---

### Post by ajgreeny on 2005-11-19
Many thanks mlomker.

I'd nearly got it right but I was adding the same option data in the linux line as for the other disk, and that just seemed to be ignored, at least it didn't mount the non active ubuntu version as I wanted.

All now working  just as I was looking for!

Many thanks again.

---

