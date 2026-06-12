---
title: "dell latitude &amp; external dvd burner problems"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by itguru3 on 2007-10-26
Hi, 

I have a dHELL Latitude d610 and I cannot seem to get it to work with my external dvd burner.  Even if it is not fully 'officially' supported, I *know* there is a way to get it to work with ubuntu, because it was working on a fedora 5 box not too long ago.  It is an HP dvd740 DVD-writer (with lightscribe).  I do not care if I get lightscribe working on linux or not, although it would certainly be cool.  

$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 03f0:8204 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

I also have an HP printer connected through USB, so I am not sure which device this is.  When I go into Device Manager I do not see my burner although it may show up as a block device (?).  The printer is listed.  

I just want to get the os to see the burner.  Once I pass that step I can worry about the application (in this case k3b which I love and usually works great) and making sure that it also recognizes the drive.  First things first.

Any help is appreciated
Thanks,
Marc

---

### Post by mdlueck on 2008-03-20
Terminal Window
cd /dev
ls -al|grep cd

Devices for the CD ROM will show up, some will be group "cdrom"

Assuming this is the second drive on the system, you might have to manually add a mount point in /etc/fstab - Use the internal drive as reference. Internal drive might be something like /dev/scd0 and the new external one might be scd1. The above ls command should return enough results that you can figure out which drive is what /dev/ entry.

---

