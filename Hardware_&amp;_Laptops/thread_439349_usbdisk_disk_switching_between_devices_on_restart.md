---
title: "usbdisk disk switching between devices on restart"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by satbunny on 2007-05-10
Hi!

I have a usb external drive plugged into a Xubuntu 6.10 server.
It is sda1 and I mount it in fstab accordingly.
Today I had to reboot, and when the machine restarted there was no sda, rather the drive had mounted as sdb1! My fstab, accordingly, failed to mount the drive correctly and since it had samba shares on it various shared drives went off the network.
Now I don't reboot often, this is a family network and yet I can keep it running. BUT sometimes a reboot is necessary or a power cut may shut down the machines.

How do I keep the same device mapped to the same USB device in such a situation?

I also have a usb dvd drive on the same server, and a floppy drive (lol) but they map as sdc and sdc0 consistently.

I notice that when I installed Edgy it created some unique identifers  for the hard discs, can something similar be done for usb disks? 

Links to any resources to address this issue are very welcome.

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ba9a7b38-6910-4741-b440-b4c89e23c083 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a772a16f-e830-4a59-8156-3eae329c3d58 none            swap    sw              0       0
/dev/hdb1	/media/30G	ext3	defaults	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc        /media/floppy1  auto    rw,user,noauto  0       0
/dev/sdb1	/media/usbdisk	ext3	defaults	0	0




:KS

---

### Post by rockdon on 2007-05-10
This is happening because of udev. What you're going to want to do is create a local ruleset for udev to manage the usb devices.

See this thread for how to do it: [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

### Post by satbunny on 2007-05-10
Thanks.

I found another answer, which is to not mount by /dev/sdb1 or whatever in the fstab but by the alias in the /dev/disk/by-id directory.

My fstab therefore now reads..

/dev/disk/by-id/ID_DRIVE /media/usbdisk etc..

It's a bit easier than the udev ruleset.

---

