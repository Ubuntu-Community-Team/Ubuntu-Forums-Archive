---
title: "External hard drive damage"
date: 2010-05-31
forum: Hardware
---

### Post by biubidboy on 2010-05-31
Hello everyone.

I recently installed Ubuntu 10.04 on a Western Digital My Passport external hard drive, and it was happily working until I knocked the hard drive off the tower of my computer on to the ground while it was running. I lost the background of my desktop and all my icons disappeared, but I managed to reboot the system and now it seems to be working fine. I ran fsck to try to fix any errors, however, I still get the following output when I run "dmesg | grep error":
```
[   55.532043] end_request: I/O error, dev fd0, sector 0
[   55.588046] end_request: I/O error, dev fd0, sector 0
```Is there anything I can do to fix these errors and, if I can't, is the hard drive still usable reliably? 
Thanks for your time,
Michael.

---

### Post by linuxisfree on 2010-05-31
> **biubidboy said:**
> Hello everyone.
 
I recently installed Ubuntu 10.04 on a Western Digital My Passport external hard drive, and it was happily working until I knocked the hard drive off the tower of my computer on to the ground while it was running. I lost the background of my desktop and all my icons disappeared, but I managed to reboot the system and now it seems to be working fine. I ran fsck to try to fix any errors, however, I still get the following output when I run "dmesg | grep error":
```
[   55.532043] end_request: I/O error, dev fd0, sector 0
[   55.588046] end_request: I/O error, dev fd0, sector 0
```Is there anything I can do to fix these errors and, if I can't, is the hard drive still usable reliably? 
Thanks for your time,
Michael.
 
 
Hi Michael,
 
I think its still a bit usable (although, not sure about the reliably part), but i'd definitely back up the data in that drive as soon as possible, just to be on the safe side.

---

### Post by jflaker on 2010-05-31
> **biubidboy said:**
> Hello everyone.

I recently installed Ubuntu 10.04 on a Western Digital My Passport external hard drive, and it was happily working until I knocked the hard drive off the tower of my computer on to the ground while it was running. I lost the background of my desktop and all my icons disappeared, but I managed to reboot the system and now it seems to be working fine. I ran fsck to try to fix any errors, however, I still get the following output when I run "dmesg | grep error":
```
[   55.532043] end_request: I/O error, dev fd0, sector 0
[   55.588046] end_request: I/O error, dev fd0, sector 0
```Is there anything I can do to fix these errors and, if I can't, is the hard drive still usable reliably? 
Thanks for your time,
Michael.

My suggestion:
Pull the data from the drive to another storage medium
wipe the drive
Replace the drive in the enclosure or buy a complete replacement
VELCRO the unit to prevent another accident.

Sorry...once a running drive falls, there is a likelyhood the heads scraped the platters and caused permanent damage to both the platters and the read/write head.

I just had that problem with a drive in a USB drive in an enclosure....That drive was completely destroyed internally (the head fell off) as it fell hard.

---

### Post by biubidboy on 2010-05-31
Thanks for the quick reply! 
Backup isn't really an issue for me right now, as I have just begun using Ubuntu so I have no important files on the system. What worries me is that I may not be able to use the external hard drive without having random crashes and data loss in the future, when I do have important files on there. Would you recommend buying a new hard drive?\

EDIT: Ahh. jflaker seems to have answered my question already. Thanks.

---

### Post by linuxisfree on 2010-05-31
I definitely would. After something like that, you REALLY never know when it'll just fail (which would REALLY HURT if you had very important data in there!)

---

### Post by biubidboy on 2010-05-31
Sound advice. Do you think that this kind of thing would be covered under warranty, or wouldn't WD replace the drive, seeing as it still appears to work with only minor damage?

---

### Post by linuxisfree on 2010-05-31
> **biubidboy said:**
> Sound advice. Do you think that this kind of thing would be covered under warranty, or wouldn't WD replace the drive, seeing as it still appears to work with only minor damage?
 
Honestly, i'm not sure... but let's hope it's covered and/or they would replace the drive. :)

---

### Post by jflaker on 2010-05-31
> **biubidboy said:**
> Sound advice. Do you think that this kind of thing would be covered under warranty, or wouldn't WD replace the drive, seeing as it still appears to work with only minor damage?

If there is no apparent damage to the drive case, you can claim that the drive started reporting errors.  I would seek a warranty replacement.

Be sure to boot n nuke the drive before returning it [http://www.dban.org/]("http://www.dban.org/")

---

### Post by jflaker on 2010-05-31
> **jflaker said:**
> If there is no apparent damage to the drive case, you can claim that the drive started reporting errors.  I would seek a warranty replacement.

Be sure to boot n nuke the drive before returning it [http://www.dban.org/]("http://www.dban.org/")

AH!  Use extreme caution with this wipe as you can accidentally wipe the wrong drive irreversibly

---

