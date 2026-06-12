---
title: "Can write to DVD, CD.  Cannot read to rip or play"
date: 2009-06-25
forum: Hardware
---

### Post by Cornbreadly on 2009-06-25
I do not know what the issue is.  The settings in my fstab for the combo drive are default.  I have pointed handbrake, acidrip, dvd::rip to both the mount point (media/cdrom0) and the /dev/scd0.

The movie shows and mounts in my computer.  The title shows up, I guess that would be the label  It recognizes blank dvds and cds.  I know the ripping programs and VLC would work if they could find it.

My fstab.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8a547bd5-df0f-4a60-897c-8f7fad307ccc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=6dbb7413-9438-46e1-9196-727a4a88d1db /home           ext3    nodev,nosuid,relatime        0       2
# /dev/sdb7
UUID=8eed6bb1-6ff8-4873-bdbc-838681e98be5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb5	/media/Media1TB	ext3	relatime,auto,users,rw	0	0		
/dev/sdb5	/medis/ntfs85gb	ntfs-3g	auto,umask=000	0	0
```

I know I missed something stupid.  Help is appreciated.  Thanks

---

### Post by Cornbreadly on 2009-06-27
PLeae help or direct me to the proper forum.  I picked hardware cause only my combo drive is not working correctly.  Thank you

---

### Post by Cornbreadly on 2009-06-28
I still do not know what this issue is.  Here is the devices hardware info from the "lshw command.
```
id:	
cdrom
description: 	DVD-RAM writer
product: 	DRW-22B1ST
vendor: 	ASUS
physical id: 	
0.0.0
bus info: 	
scsi@2:0.0.0
logical name: 	
/dev/cdrom
logical name: 	
/dev/cdrw
logical name: 	
/dev/dvd
logical name: 	
/dev/dvdrw
logical name: 	
/dev/scd0
logical name: 	
/dev/sr0
logical name: 	
/media/cdrom0
version: 	1.00
capabilities: 	removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:	
ansiversion	=	5
mount.fstype	=	udf
mount.options	=	ro,nosuid,nodev,utf8
state	=	mounted
status	=	ready
```

---

### Post by Cornbreadly on 2009-06-28
I tried with dvd::rip with all of the logical names listed above.  Am I missing a library?  I have libdvdcss2.

---

### Post by mc4man on 2009-06-29
You should post what version of ubuntu you're using

Everything you posted looks good, though the lshw is not quite as informative/linear as it could be (try this with a dvd in the drive

sudo lshw -C disk

Anyway it shows 
> mount.fstype	=	udf ([COLOR="Blue"]udf filesystem mounted as it should[/COLOR]
mount.options	=	ro,nosuid,nodev,utf8 ([COLOR="Blue"]all good here and below[/COLOR]
state	=	mounted
status	=	ready

With the dvd still in the drive do this and see what happens and or post terminal output
```

vlc dvd://
```

Before doing anything go into home folder ( view -> show hidden files) and delete the .dvdcss folder (good first step for dvd troubleshoot

If you think it's a decrypting  issue than start vlc like this and look for vlc_output.log in home folder (also delete .dvdcss folder first & w/ dvd in the drive

```
export DVDCSS_VERBOSE=2 && vlc dvd:// >  vlc_output.log 2>&1
```

---

### Post by Cornbreadly on 2009-07-05
Wanted to let you know the deleting the .dvdcss folder worked like magic.  Thank you so much

---

