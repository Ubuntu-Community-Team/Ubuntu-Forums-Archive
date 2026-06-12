---
title: "DVD Rom Trouble"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by glidetothehoop on 2005-04-06
I'm a Ubuntu newbie (using 5.04), but have had some basic experience using and installing Knoppix before.  I've run the Ubuntu system updater so all the latest core files are installed to 5.04.

I'm having trouble getting Ubuntu to recognize the DVD-Rom drive in the computer.  The system used this same drive to install Ubuntu, so I don't doubt that it is functioning.  My drive set up is the following....

I have two hard drives on the primary IDE controller

The DVD-Rom drive is the first drive on the Secondary IDE
and a CD-RW drive is the second drive on the Secondary IDE drive.

When I look in the Media folder I see a cdrom0 and cdrom1, but no DVD.

The CD-RW drive automounts when loading data or audio cds just fine.

The DVD-Rom drive doesn't mount or play or even recognize any media that is placed into it (DVD or CD).

Any help would sure be appreciated.

Sincerely,

Greg.

---

### Post by dusu on 2005-04-08
can you tell us what your /etc/fstab file looks like ?

---

### Post by glidetothehoop on 2005-04-11
Sorry for the delay in reply.  After doing a couple of Ubuntu system updates the DVD problem has "gone away".

My FSTAB is below.  Now I'm having trouble mount HDB1

[FONT=Courier New]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1	/               ext3    defaults        0       2	
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 rw,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/FONT]

---

### Post by jeremy on 2005-04-11
/dev/hdb1 / ext3 defaults 0 2   <- you are trying to mount hdb1 to the same place as hda1 ie. / 
you should create a folder in /media, call it, say, /media/hdb then change the line to read
/dev/hdb1 /media/hdb ext3 defaults 0 2

---

### Post by garnertr on 2005-05-12
I'm having the same problem:

/etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 rw,user,noauto  0       0

mount /media/cdrom0:
mount: block device /dev/hdc is write-protected, mounting read-only


dmesg | tail -5:

hdc: status error: error=0x00
hdc: drive not ready for command
cdrom: This disc doesn't have any tracks I recognize!
hdc: status error: status=0x00 { }
hdc: status error: error=0x00

---

