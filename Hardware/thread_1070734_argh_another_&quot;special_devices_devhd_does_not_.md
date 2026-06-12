---
title: "argh: another &quot;special devices /dev/hd* does not exist&quot; mount error!"
date: 2009-02-15
forum: Hardware
---

### Post by rmhurt on 2009-02-15
i'm trying to switch from a poorly-maintained Gentoo mythtv box to MythBuntu, which is why i'm posting here instead of in a Gentoo forum.  i have a new 1TB hd with MythBuntu installed on it while the Gentoo box is made up of 3 harddrives which total 950GB (and it's running kernel 2.6.21-r4).  the majority of the Gentoo is an LVM file system mounted to /mnt/video which is where all the videos are that i want to copy to the MythBuntu hd.  because i'm not very familiar with the LVM system, my plan is to start Gentoo with the MythBuntu hd as a slave, mount it, and then copy all the video files to it.

when Gentoo boots up i see some errors with the new hd, recognized as /dev/hdd.  (hda,hdb & hdc are the 3 existing Gentoo hds.)  the errors appear in dmesg as:

```

hdd: max request size: 512KiB
hdd: 1953525168 sectors (1000204 MB) w/32767KiB Cache, CHS=65535/255/63, UDMA(133)
hdd: cache flushes supported
 hdd:hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hdd: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown
<..a dozen or so of the 2 dma_intr errors snipped..>
 unable to read partition table

```

when Gentoo has fully booted, /dev/hdd is visible but as superuser the command 'fdisk -l' doesn't show /dev/hdd in its output.  what??  but 'hdparm -I /dev/hdd' shows detailed information about it, and i discovered fdisk is now happy:

```

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   83  Linux
/dev/hda2               6          68      506047+  83  Linux
/dev/hda3              69        1528    11727450   83  Linux
/dev/hda4            1529       24321   183084772+  8e  Linux LVM

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb doesn't contain a valid partition table

Disk /dev/hdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdc doesn't contain a valid partition table
[COLOR="Navy"]
Disk /dev/hdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1459    11719386   83  Linux
/dev/hdd2            1460      121601   965040615    5  Extended
/dev/hdd5            1460        1583      995998+  82  Linux swap / Solaris
/dev/hdd6            1584      121601   964044553+  83  Linux
[/COLOR]

```
that was scary, but it now seems like i should be able to mount /dev/hdd6 to the new /mnt/mythbuntu folder i created for it.  from the fstab file in the MythBuntu system i know that hdd6 is file system 'xfs' with mount point '/var/lib'.

```

mythtv ~ # ls -l /mnt
total 36
drwx------ 2 root root  4096 Mar 10  2005 cdrom
drwxr-xr-x 2 root root  4096 Jan 30 13:52 dvd
drwx------ 2 root root  4096 Mar 10  2005 floppy
drwxr-xr-x 2 root root  4096 Feb 14 17:39 mythbuntu
drwxr-xr-x 2 root root 16384 Feb 14 13:33 video

mythtv ~ # mount -t xfs /dev/hdd6 /mnt/mythbuntu
mount: special device /dev/hdd6 does not exist

```

after reading many of the forum posts regarding the many ways one can see the "does not exist" error, i think there may be a work-around by adding /dev/hdd6 to Gentoo's /etc/fstab file with super-secret options, but if that's true the options are beyond me.  i tried the following 3 lines (and some others, but one at a time) in fstab but the ensuing 'mount -a' always spits out the "does not exist" error.

```

/dev/hdd6 /mnt/mythbuntu xfs defaults 0 0
/dev/hdd6 /mnt/mythbuntu xfs user,rw,users,umask=0000 0 0
/dev/hdd6 /mnt/mythbuntu xfs noatime 0 0

```

help!  ](*,)

---

### Post by cariboo on 2009-02-15
This may sound like a dumb question, but are you sure that /dev/hdd is formated as xfs?

Jim

---

### Post by rmhurt on 2009-02-15
> **cariboo907 said:**
> This may sound like a dumb question, but are you sure that /dev/hdd is formated as xfs?


i'm pretty sure.  when i run MythBuntu, /etc/fstab looks like this:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc  /proc  proc  defaults  0 0

# /dev/sda1
UUID=55cb673d-8cde-46e9-8f02-635aa842cb77 /  ext3  errors=remount-ro  0 1

# /dev/sda6
UUID=60bf28c8-feb2-462a-a90e-844f96cbd078  /var/lib  xfs  defaults  0 2

# /dev/sda5
UUID=430ef83a-1fa5-45ea-98df-c0a14a4d15f4  none  swap  sw  0 0

```

and i installed and ran GPartEd which seconded the notion. i'm assuming /dev/sda6 on MythBuntu is /dev/hdd6 on Gentoo.  but i also tried to mount it as type ext3 with no luck.

---

