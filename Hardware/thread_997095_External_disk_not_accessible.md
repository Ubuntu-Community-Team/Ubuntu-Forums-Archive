---
title: "External disk not accessible"
date: 2008-11-29
forum: Hardware
---

### Post by former_warper on 2008-11-29
My wife has a Fujitsu-Siemens Storagebird Solo 35-UB 1TB USB drive.  She backed up about 100GB of data onto it.  She connects it to a Gateway laptop running Windoze XP Media Center Edition.  Yeah, yeah, I know!

She encountered the BSOD yesterday.  The drive was connected, but she did not have any files on the drive open.  When the system came back up, she couldn't read the drive at all.  The blue light was on, and the system said it was connected, and even the compmgmt.msc reported it connected, with the correct size and file system.  However, via the properties button through Explorer I could not get the volumes to populate.  When I took it off her system, I was able to force it to "safely remove" before disconnecting it.

Worried that prolonged use of M$ might affect my health, I hooked up the external drive to my trusty Ubuntu Gateway 7405GX.  I can't even see it! I can feel it spinning, but I cannot see if it's trying to connect to it. 

I've tried sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force. 

I am not sure exactly what could have happened to her drive.  I suspect the SATA controller or cache on drive has been affected.  I just want to get to the data and make sure it's still readable so I can make DVD backups of it.

What else can I try?  Is there any way to see what is happening - it is trying to read the MBR on it, or is index it?  Are there any utilities I can try?

---

### Post by finito on 2008-11-29
Try restarting windows in safe mode and try using the drive there.

---

### Post by cariboo on 2008-11-29
Can you paste the output of dmesg when you plug the drive in, in your next post. To do so open a Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n 10
```

This will print the last 10 lines of /var/log/dmesg.

Jim

---

