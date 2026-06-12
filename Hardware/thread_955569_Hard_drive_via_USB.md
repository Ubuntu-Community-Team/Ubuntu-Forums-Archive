---
title: "Hard drive via USB"
date: 2008-10-22
forum: Hardware
---

### Post by naugiedoggie on 2008-10-22
Hello,

I have an old HD that I want to mount just to recover some data stored there.  I put this drive in an "external drive case" that plugs into USB.  The drive does not automount.  I have another, similar drive, that does automount in the same circumstance.

The drive is quite old, circa 2000, and had/has slackware on it.  I'm guessing it is ext2, but I can't remember now.

I don't know any tools to use to detect and troubleshoot this drive over USB.  Are there any?  I prefer not to put it back into a case, although it's not out of the question.

Thanks.

mp

---

### Post by chris_nava on 2008-10-22
Check the jumpers on the drive... Most external cases require that the drive be configured as "master" not "slave".

---

### Post by naugiedoggie on 2008-10-22
> **chris_nava said:**
> Check the jumpers on the drive... Most external cases require that the drive be configured as "master" not "slave".

Hello,

Good try.  I tested all three settings -- CS, master, slave ... no joy.  The drive shows up when checked via lsusb.    

```
root@cecilia:~# lsusb
Bus 002 Device 018: ID 067b:3507 Prolific Technology, Inc. PL3507 ATAPI6 Bridge 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

It may be toasted.  It's been sitting in my closet since about 2003.  But it was working when I put it away.

Thanks.

mp

---

### Post by chris_nava on 2008-10-29
Try using "Partition editor" to see if the machine can see the drive.  It should show up as a /dev/sd[X] device (but your main HD will also so be careful.)

If the editor sees the drive but it will not mount then you may need to partition/format it.  This WILL ERASE all data on the drive but may make it usable for storage.

Remember: Be careful what you "apply" as Partition Editor can be a destructive tool.

---

### Post by naugiedoggie on 2008-10-30
> **chris_nava said:**
> Try using "Partition editor" to see if the machine can see the drive.  It should show up as a /dev/sd[X] device (but your main HD will also so be careful.)

If the editor sees the drive but it will not mount then you may need to partition/format it.  This WILL ERASE all data on the drive but may make it usable for storage.

Remember: Be careful what you "apply" as Partition Editor can be a destructive tool.

Thanks for the useful tip.  parted doesn't see the drive, it only sees the main drive.  I guess that is a clue that the drive is majorly dead.  It spins up, doesn't make any 'click of death' types of noises or whining, but otherwise, no joy.

Thanks.

mp

---

### Post by likuidkewl on 2008-10-30
What version of Ubuntu are you using?  If it is 8.10 there is a known bug with USB drives.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789)

Have a look in the syslog and see if there are constant Sense messages too.

---

