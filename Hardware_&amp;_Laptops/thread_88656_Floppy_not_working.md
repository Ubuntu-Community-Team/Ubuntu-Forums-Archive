---
title: "Floppy not working"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by WBC on 2005-11-10
Hello,
I have been working with Ubuntu Breezy Badger which is the server distro 5.10.

I can not get the floppy drive to work.
This is all from the command line.

So far I can get the drive to lite up and spin and read a little but I can not use it.  I tried the following commands (below) and am posting the results below each command.
=======================================================
To see what is in the Fstab file.
---
$ cat /etc/fstab
results = /dev/fd0    /media/floppy0    auto    rw,user,noauto    0    0
=======================================================
Mounting the floppy drive.
---
$ mount  -t vfat /dev/fd0
results = I could not determine the file system type, and none was specified.
=======================================================
A second attempt to mount the floppy.
---
$ sudo mount -t vfat /dev/fd0  /floppy
results = mount: /dev/fd0 is not a valid block device

NOTE:   /floppy exists
========================================================

Anyone have any ideas?  :???: 
I just need a floppy drive to use?

WBC

---

### Post by Kyral on 2005-11-10
try 

```
mount /media/floppy0
```

---

### Post by WBC on 2005-11-10
[QUOTE=Kyral]try 

```
mount /media/floppy0
```[/QUOTE]
command: mount /media/floppy0

results = mount: Icould not determine the file system type, and none was specified.

=======================================================
command: mount -t vfat /dev/fd0 /mnt/floppy

results = mount: /dev/fd0 is not a valid block device.

Note: a DOS (fat) formatted floppy was in the drive.

=======================================================

---

### Post by michael_salcher on 2005-11-10
you should probably seriously consider not using floppies anymore. i haven't used floppies for years. just burn everything on a cd-rw.

---

### Post by muchio on 2005-11-11
[QUOTE=michael_salcher]you should probably seriously consider not using floppies anymore. i haven't used floppies for years. just burn everything on a cd-rw.[/QUOTE]
:eek: Strange advice... Anyway, I have the same problem with the NEC usb floppy device - unable to mount.

---

### Post by jdtanner on 2005-11-11
There seems to be a problem for some people with mounting removable media. Have you tried updating you version of pmount (see link below). This sorted out some of my problems, but didn't sort out the automounting issue with my cdrom :-(

[http://www.ubuntuforums.org/showthread.php?t=88000&highlight=pmount+dapper](http://www.ubuntuforums.org/showthread.php?t=88000&highlight=pmount+dapper)

Cheers,
JohnT

---

### Post by canadianwriterman on 2005-11-11
[QUOTE=jdtanner]There seems to be a problem for some people with mounting removable media. Have you tried updating you version of pmount (see link below). This sorted out some of my problems, but didn't sort out the automounting issue with my cdrom :-(

[http://www.ubuntuforums.org/showthread.php?t=88000&highlight=pmount+dapper](http://www.ubuntuforums.org/showthread.php?t=88000&highlight=pmount+dapper)

Cheers,
JohnT[/QUOTE]

This was a fix to pmount that worked perfectly for me.

---

