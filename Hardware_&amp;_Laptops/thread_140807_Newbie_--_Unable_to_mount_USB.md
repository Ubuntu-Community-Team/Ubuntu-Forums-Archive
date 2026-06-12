---
title: "Newbie -- Unable to mount USB"
date: 2006-03-07
forum: Hardware &amp; Laptops
---

### Post by keka on 2006-03-07
Hello, i am very new to Linux, (3 days )

when i plug my USB flash I can see it in my Computer, but unable to mount it (by double clicking)

read a few forums but with no results.

this is what is get when i double click
______________________________________
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
_______________________________________

this is my /etc/fstab with USB pluged in
-------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

--------------------------------------------------------

both falsh drives were used with win and have files on them, i formated one with win "fat32"

Please reply because my wife is very upset, one of the drives is hers!

---

### Post by Sutekh on 2006-03-07
You need to add a line to your fstab for the USB, because at the moment there isn't one.

[QUOTE=keka]mount: wrong fs type, bad option, bad superblock on /dev/sdb,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so[/QUOTE]
I'll assume that the USB is /dev/sdb1, but you can determine this better by using
```
sudo fdisk -l
```
Once you know the name of the USB (still assuming its /dev/sdb1), you can edit your **/etc/fstab**.  

You should create a backup of the fstab before editing it
```
sudo cp /etc/fstab /etc/fstab_backup
```
Then you can edit it using **gedit, nano**, whatever you wish
```
sudo gedit /etc/fstab
```
Once you have opened the fstab then you need to add the line to mount the shared drive.  You said one was formatted FAT32, what about the other?

**If the drive is formatted FAT32**, you should add a line similar to this one
```
[COLOR="Blue"]/dev/sdb1[/COLOR]    [COLOR="Red"]/media/windows[/COLOR]   [COLOR="Green"]vfat[/COLOR]   [COLOR="DarkOrchid"]iocharset=utf8,umask=0000[/COLOR]   0   0
```
 - [COLOR="Blue"]/dev/sdb1[/COLOR] - is the location of the shared drive, you will have to edit this as apropriate

 - [COLOR="Red"]/media/windows[/COLOR] - this is the folder where the drive will be *mounted*.  If this folder doesn't exist you will need to create it yourself ```
sudo mkdir [COLOR="Red"]/media/windows[/COLOR]
```
**Note** you don't have to use [COLOR="Red"]/media/windows[/COLOR], in my system I use [COLOR="Red"]/mnt/os-shared[/COLOR], its up to you

 - [COLOR="Green"]vfat[/COLOR] - this specifies the filesystem as fat

 - [COLOR="DarkOrchid"]iocharset=utf8,umask=0222[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask**.  [COLOR="DarkOrchid"]umask=0000[/COLOR] allows read, write and execute access to the partition.


Once you've modified the /etc/fstab, you can save it and issue the command```
sudo mount -a
```This re-mounts the partitions, without you having to restart your computer.

---

### Post by keka on 2006-03-07
Thanks Sutekh for your detailed reply. Buy I am still having difficulties.

after carefuly fallowing your instructions i get this

sudo mount -a
mount: special device /dev/sdb1 does not exis
---------------------

sudo fdisk -l
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4677    37567971   83  Linux
/dev/hda2            4678        4865     1510110    5  Extended
/dev/hda5            4678        4865     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         992      999813+   6  FAT16
----------------------------------------------------------------------

 sudo gedit /etc/fstab
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sdb1    /media/os-shared   vfat   iocharset=utf8,umask=0000   0   0
-----------------------------------------------------------------------

---

### Post by taurus on 2006-03-07
Try using /dev/sda1 then...

---

### Post by keka on 2006-03-07
Thanks Taurus, this is really dumb of me! how could i not see that it is sda1 and not sdb1!  Maybe Ishould stick to WINDOWS !

Thanks again all of you !

---

### Post by keka on 2006-03-07
My last question is this. My wife will defenetly complain about mounting her USB all the time, is there a possibility for OS to recognize it on it's on?

---

### Post by skirkpatrick on 2006-03-07
My machine automounts it without me having to do anything.  The only problem I've found is that something with my cables doesn't allow me to run USB 2.0 out the front of my machine.

---

### Post by taurus on 2006-03-07
[QUOTE=keka]My last question is this. My wife will defenetly complain about mounting her USB all the time, is there a possibility for OS to recognize it on it's on?[/QUOTE]
If you want Ubuntu to automount it when you insert it, then you need to modify your /etc/fstab.
```

/dev/sda1    /media/windows   vfat   iocharset=utf8,umask=0000   0   0

```

---

### Post by skirkpatrick on 2006-03-09
Really?  Cause mine automounts and I don't have anything for it in /etc/fstab.  In fact, it has automounted since I installed Breezy without me doing anything.

---

### Post by russelld on 2006-05-15
in my laptop, usb devices mount in the LiveCD, but have to have this fstab config in order to work..........

It would be so nice to have this automounter/usb stuff sorted out.

Maybe a good howto could be written to get it working! 

BTW the devs for the usb in this box were found in /dev/.static/dev/sda*,  and after the fstab was edited, then usb automount worked! 
```

/dev/.static/dev/sda1   /media/usb1	ext3	          rw,user,exec               0       0
/dev/.static/dev/sda2	/media/usb2	ext3		  rw,user,exec               0       0
/dev/.static/dev/sda3	/media/usb3	ext3		  rw,user,exec               0       0
/dev/.static/dev/sda4	/media/usb4	ext3		  rw,user,exec               0       0
/dev/.static/dev/sda5	/media/usb5	ext3		  rw,user,exec               0       0
/dev/.static/dev/sda6	/media/usb6	ext3		  rw,user,exec               0       0
/dev/.static/dev/sda7	/media/usb7	ext3		  rw,user,exec               0       0
/dev/.static/dev/sda8	/media/usb8	ext3		  rw,user,exec               0       0
/dev/.static/dev/sda9	/media/usb9	ext3		  rw,user,exec               0       0
/dev/.static/dev/sda10	/media/usb10	ext3		  rw,user,exec               0       0

```

---

