---
title: "Problem with DVD-RW"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by drblah on 2008-01-02
I have just installed Ubuntu on my laptop (Znote 6625WD) but Ubuntu won’t access my DVD-RW drive. When I attempt to access it I get this message:” Can not mount the selected drive. Mount: special device /dev/scd0 does not exist”



Last time I installed Ubuntu it made the drive inaccessible even from Windows.



What can I do to fix this? I am new to Ubuntu (aka haven't used anything but Windows my whole life) so I don’t have any idea of how to fix this.

---

### Post by logos34 on 2008-01-02
you can't read cds or dvds, or just dvds?  Is this a data dvd or movie?

---

### Post by Yellow Pasque on 2008-01-02
gedit /etc/fstab and paste it here. We've been getting a lot of these inaccessible DVD-R drive lately :\

EDIT: Also do a 
sudo lshw -C disk
and post the info it spits out for the CD drive (we don't need the sections about hard disks)

---

### Post by drblah on 2008-01-02
@ logos34 I can't access the drive. It is like the drive is not installed.

Here is the fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5f71fa92-0b61-41f8-80d8-96ffce6af88f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=30558422-ac81-4460-9afa-1e46dbfe6ec1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by Yellow Pasque on 2008-01-02
A useful utility is cdrecord. (sudo apt-get install cdrecord)
Then you can probe with
```
sudo cdrecord --scanbus
```
Or
```
sudo cdrecord --driveropts=help --checkdrive
```

---

### Post by drblah on 2008-01-02
When i run

```
 sudo cdrecord --checkdrive 
```

I get:

```
 Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
Linux sg driver version: 3.5.34
Using libscg version 'schily-0.9'.
No target specified, trying to find one...
cdrecord: Success. Cannot open or use SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.

```

It appears to be a driver problem as far as i can tell.

---

### Post by Yellow Pasque on 2008-01-02
:\
I'm not sure if you saw my edit, so I'll ask you to run this command again to see if it's recognizing the drive at all. (This is a SATA burner, right?)
```
sudo lshw -C disk
```

---

### Post by drblah on 2008-01-02
It only gives some info about my hard drive. I don't think my burner is SATA but i don't know.

---

### Post by Yellow Pasque on 2008-01-02
Seen this thread?
[http://ubuntuforums.org/showthread.php?t=647330&highlight=Znote+6625WD](http://ubuntuforums.org/showthread.php?t=647330&highlight=Znote+6625WD)

---

### Post by drblah on 2008-01-02
This is exactly the same problem. It appears to be caused by Grub. Do you know if there is a fix for it or do i just have to install Lilo instead? I don't like the option with the IDE-channel because I won't be able to boot from the DVD drive.

Oh and thanks.

---

### Post by Jeanpaul145 on 2008-06-18
> **drblah said:**
> This is exactly the same problem. It appears to be caused by Grub. Do you know if there is a fix for it or do i just have to install Lilo instead? I don't like the option with the IDE-channel because I won't be able to boot from the DVD drive.

Oh and thanks.

I have a zepto znote 6625WD as well, and experiencing the same problem.
I don't think this problem is caused by Grub.
You see, it also happens in Windows, as well as Linux.
It is (AFAIK) a nasty bug in the BIOS that's causing this.

Short-term fix:
Try changing the BIOS settings so that the cdrom drive (either primary or secondary slave) is set to NONE instead of AUTO or CDROM. Then try bootring Linux/windows and accessing the drive again. It worked for me!

btw: this makes your drive inaccessible for bootable optical media. To boot from a disk, simply change the setting back to CDROM.

Long-term fix:
Everybody who is experiencing this bug, PLEASE send mails to zepto asking them to fix this! The BIOS isn't exactly open source, so they are the only ones who CAN fix this.

---

