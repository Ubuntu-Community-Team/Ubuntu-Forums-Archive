---
title: "Locate Winxp Hard Drive"
date: 2005-02-20
forum: Hardware &amp; Laptops
---

### Post by desi on 2005-02-20
hello!
I successfully installed Ubuntu. My system has 2 hard drives. I have Winxp on hda and put ubuntu on hdb.
When I start the computer, Grub gives me the option & I'm able to choose the OS - all works well. :wink: 
I'm however unable to locate the Windows hard disk when I boot into Ubuntu - where many music files are stored...
Went here: [http://www.ubuntuguide.org/#mountunmountfat](http://www.ubuntuguide.org/#mountunmountfat) and followed directions.

Q: How to mount Windows partition (FAT) on boot-up, and allow all users to read/write?

   1. Read General Notes
   2.      e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT)
           Local mount folder: /media/windows
   3. Read How to list the partition tables?
   4.
      $ sudo mkdir /media/windows
      $ sudo cp /etc/fstab /etc/fstab_backup
      $ sudo gedit /etc/fstab
   5. Append the following line at the end of file
      /dev/hda1       /media/windows    vfat    umask=000       0       0
   6. Save the edited file (sample)
   7. Read How to remount /etc/fstab without rebooting?

And then, did this:
Q: How to remount /etc/fstab without rebooting?

   1. Read General Notes
   2.   $ sudo mount -a

Got this msg:

keshav@home:~ $ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       or too many mounted file systems
Any suggestions, help would be greatly appreciated.
Many thanks in advance

KB

---

### Post by Buffalo Soldier on 2005-02-20
What type of filesystem is used for the Windows XP partition? NTFS or FAT32?

If it's NTFS (default install of Windows XP uses NTFS) then you should be reading [http://ubuntuguide.org/#automount**ntfs**](http://ubuntuguide.org/#automount**ntfs**) where it states you should be adding this line to your fstab:

```
 /dev/hda1       /media/windows    **ntfs**    umask=**0222**      0       0
```

Please bear in mind that Microsft keeps the details of NTFS filesystem very closed. Therefore linux only manage to read files in NTFS partitions but not write.

---

### Post by ToS on 2005-02-21
[QUOTE=Buffalo Soldier]What type of filesystem is used for the Windows XP partition? NTFS or FAT32?

If it's NTFS (default install of Windows XP uses NTFS) then you should be reading [http://ubuntuguide.org/#automount**ntfs**](http://ubuntuguide.org/#automount**ntfs**) where it states you should be adding this line to your fstab:

```
 /dev/hda1       /media/windows    **ntfs**    umask=**0222**      0       0
```

Please bear in mind that Microsft keeps the details of NTFS filesystem very closed. Therefore linux only manage to read files in NTFS partitions but not write.[/QUOTE]
 If you run "fdisk -l", you should be able to find your windows partition and determine the proper filesystem type to put in fstab.

---

