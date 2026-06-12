---
title: "Trouble enabling DVD part of combo drive - check my fstab file"
date: 2008-12-17
forum: Hardware
---

### Post by benj12 on 2008-12-17
Good afternoon friends,

I'm having a peculiar problem with a brand new install of Ubuntu on my Dell 600m laptop.  My laptop features a Dvd-rw/Cd-rw (whatever the technical name for the combo drive is...).  The system will mount/burn CDs, but when I stick in a DVD or blank DVD, it spins up for seconds, then stops and nothing happens.  I'm suspecting this is a configuration problem, because the drive w/DVDs functions normally under Windows XP.  I'm going to attach my fstab file, because from my research there might be a problem there.

Thanks in advance for any help that can be supplied.  This is my first week with Ubuntu, and I'm never looking back (unless I'll have to keep XP for DVDs...)!

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=61584adc-837b-45aa-a954-5f554e20c5f3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1776f8c4-6a6a-4c2d-8dba-81f4549f97fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


---

### Post by Ant68 on 2008-12-17
could you post the output for:
> sudo lshw -C disk

---

### Post by benj12 on 2008-12-17
> **Ant68 said:**
> could you post the output for:

Here you go, thanks for the help.

> 
kernel device tree (sysfs)
  *-disk                  
       description: ATA Disk
       product: ST980815A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: n/a
       serial: 5LYCG8FE
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d673d673
  *-cdrom
       description: DVD reader
       product: RW/DVD GCC-4243N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: A102
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc



---

### Post by Ant68 on 2008-12-17
same as for me:

capabilities: removable audio cd-r cd-rw dvd


there should be 

capabilities: removable audio cd-r cd-rw [COLOR="Red"]dvd-rw[/COLOR]

let me know if you find something (i.e a way to get it set up correctly)?

---

### Post by benj12 on 2008-12-17
> **Ant68 said:**
> same as for me:

capabilities: removable audio cd-r cd-rw dvd


there should be 

capabilities: removable audio cd-r cd-rw [COLOR="Red"]dvd-rw[/COLOR]

let me know if you find something (i.e a way to get it set up correctly)?


Yes, that is also true.  However, in my case I can't even read regular "DVDs" as the capabilities list would make you think.

I'm hoping we'll get a guru on here soon to give us some help, I've exhausted everything in my capabilities...

---

### Post by Ant68 on 2008-12-18
investingating further on my side, I am having the exact same problem. it does not even read normal video/audio dvd where it read audio cd...

I posted another request in the absolute beginner section. The guru might be there... :)

[http://ubuntuforums.org/showthread.php?t=1014674](http://ubuntuforums.org/showthread.php?t=1014674)

---

### Post by Ant68 on 2008-12-19
I did not managed to fix the issue with my dvd writer. I change hardware (driver) and the new one worked straight away. 

One additional thing I cold have tried is to upgrade the firmware. However I could not see any linux firmware for the faulty driver...

---

### Post by Ant68 on 2008-12-19
fixed the issue changing driver hardware...

---

