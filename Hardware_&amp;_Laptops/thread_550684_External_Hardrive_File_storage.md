---
title: "External Hardrive File storage"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by compsariomike on 2007-09-14
Alright...

So i have a laptop and a 250 GB seagate external hardrive.  I used to have Fiesty on the external but during the automatic disk check something was deleted and it freezes during boot up.  So i reinstalled fiesty on my main hardrive and have been salvaging all the info I can from the External.  Now that I've done that I would like to reformat the external hd and format it for file storage only and not bother with installing fiesty.  I've tried doing this through the alternate cd and simply skiping to the partitioning section.  
This worked, to an extent.  There are still some files that were installed and no matter what I do i still cant write to the external.  

So can anyone tell me how to completely reformat the external for storage?  I've been trying and have failed again and again.

Thanks

---

### Post by logos34 on 2007-09-14
umount the drive/partition.  So, for example, if it's mounted at '/media/usbdisk', then

**sudo umount /media/usbdisk**

**sudo mkfs.ext3 /dev/sdb1** (substitute your external drive for sdb1)

System>Preferences>Removable Drives and Media.  Makes sure the option 'Mount removable drives when hot-plugged' is checked.  

Reload the desktop and hopefully it will automount at the default location:
[B]
ctrl+alt+backspace[/B]

or reboot if necessary.

Right-click on the drive's desktop icon, Properties>Permissions tab.  The 'Others' line should have the Write checkbox selected. If it's not selected, you don't have permission to access the drive.

To change the permissions, in a terminal type:

**cd /media**

**ls -al**

you should see 'usbdisk' or 'disk'

**sudo chmod a+w usbdisk**

You can also add an entry in the fstab so it mounts in a specified way at boot, but you'll need to find the UUID:

**ls -l /dev/disk/by-uuid**

**gksudo gedit /etc/fstab** 

add a line so it mounts at '/media/storage' (for example):

> # Entry for /dev/sdb1 :
UUID=xxxxxxx-xxxxx-xxxxxx /media/storage ext3 defaults 0 2

**sudo mkdir /media/storage**

Or use volume labels with e2label or tune2fs:

[http://ubuntuforums.org/showthread.php?t=139535](http://ubuntuforums.org/showthread.php?t=139535)
[http://www.linux.com/base/ldp/howto/Partition/labels.htmlt](http://www.linux.com/base/ldp/howto/Partition/labels.htmlt)

---

