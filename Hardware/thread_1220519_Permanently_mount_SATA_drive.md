---
title: "Permanently mount SATA drive"
date: 2009-07-22
forum: Hardware
---

### Post by nloding on 2009-07-22
I'm confused about mounting drives and reading more articles is making me more and more confused, so hopefully someone here can spare a quick second and help me out.

I added a 1TB drive to my Ubuntu box for backups.  It's plugged into a SATA card.  I've mounted it to /nas using sudo mount /dev/sdb1 /nas ... and it works until I reboot.

So I need to edit the fstab file to make it work?  So what do I add to the fstab file?  It's formatted as one giant ext3 partition ... HELP!

---

### Post by shodai100 on 2009-07-22
----------------------------------------------------------------------------------------------------------
WARNING: THIS IS FOR EXTERNAL DRIVES.....

I am not sure if this works with internal....

found the link here

[http://www.kubuntuway.net/forum/showthread.php?t=162](http://www.kubuntuway.net/forum/showthread.php?t=162)

----------------------------------------------------------------------------------------------------------
Mounting an external hard drive permanently in ubuntu using /etc/fstab:

Backup up /etc/fstab
     Code:
     cp /etc/fstab /etc/fstab.old 

Make the mount directory
     Code:
     sudo mkdir /media/externalhd 

Plug in the hard drive and found out where it's assigned:
     Code:
     dmesg | tail 
Y
ou should see something like this:

     Code:
     [76314.955359] sd 3:0:0:0: [sdb] Write Protect is off
[76314.955367] sd 3:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[76314.955373] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[76314.956100] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[76314.956729] sd 3:0:0:0: [sdb] Write Protect is off
[76314.956736] sd 3:0:0:0: [sdb] Mode Sense: 2d 08 00 00
[76314.956741] sd 3:0:0:0: [sdb] Assuming drive cache: write through 

Now we know that the hard drive gets assigned to /dev/sdb

Open up /etc/fstab with your favorite editor:

     Code:
     sudo vi /etc/fstab 

Add this line:
     Code:
     /dev/sdb /media/externalhd vfat defaults 0 0 
Note that this works for mounting VFAT file system (most usb thumbdrives and external harddrives come preformmated with FAT32). 
If you its a different file system, you will need to change "vfat" to the appropriate name.

Now you can reboot or issue a:
     Code:
     sudo mount -a 

Now your drive should be mounted at /media/externalhd

For more info:
     Code:
     man fstab

---

