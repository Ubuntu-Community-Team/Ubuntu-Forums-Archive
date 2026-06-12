---
title: "Handheld GPS USB - Not Allowed to Write"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by shadder on 2008-03-07
I have two Magellan GPS units, an eXplorist 210 and a 400. Both of these units connect to the Computer by a USB cable. Once connected and turned on in the file transfer mode the unit is mounted as a external hard drive , an icon shows up on the desktop for it (GPSR) and a file explore window opens displaying the file structure of the unit. The problem with both units is that they are showing as read only drives. The owner of the drive is my myself (bill), file access is set to"---".  The group is set to root which has folder acccess set to none ans file access to "---". Same for Other.  Any attempt to make changes is met with the following error: "Couldn't change the permissions of "folder name" because it is on a read-only disk".  To make things more interesting the 400 unit uses an optional SD card which when inserted into the unit for the first time recreates the file structure on it. The SD card with the structure added to it also becomes read only. The drives in the units are FAT. The results of ls -l usbdisk is:

total 624
drwx------ 2 bill root  16384 2005-05-11 10:00 Background Maps
-rwx------ 1 bill root 557056 2005-05-11 10:00 CRITMEM.MEM
drwx------ 2 bill root  16384 2005-05-11 10:00 Detail Maps
drwx------ 2 bill root  16384 2005-05-11 10:00 Geocaches
?--------- ? ?    ?         ?                ? GPSR/My POIs
?--------- ? ?    ?         ?                ? GPSR/Track Logs
drwx------ 2 bill root  16384 2005-05-11 10:00 Routes
drwx------ 2 bill root  16384 2005-05-11 10:00 USBTRANS

My fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=92ccbaeb-befc-4387-b725-2ddc38c2edcb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1d86b8d5-5079-4888-a038-2583f0d98239 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


Any help would be fantastic. I've been fighting this problem for far too long now.

---

### Post by shadder on 2008-03-07
As a followup the results of MEDIA is:

bill@bill-desktop:/media$ ls -l
total 88
lrwxrwxrwx  1 root root     6 2008-01-16 12:43 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-01-16 12:43 cdrom0
drwx------ 11 bill root 32768 1969-12-31 19:00 DATA BACKUP
lrwxrwxrwx  1 root root     7 2008-01-16 12:43 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2008-01-16 12:43 floppy0
drwx------  9 bill root  8192 1969-12-31 19:00 GPSR
drwx------  3 bill root 16384 1969-12-31 19:00 WIKI


The DATA BACKUP and WIKI drives have the exact same settings but they both work fine.

---

