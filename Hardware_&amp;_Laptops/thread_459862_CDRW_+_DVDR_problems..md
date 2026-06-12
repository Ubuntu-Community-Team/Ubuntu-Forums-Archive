---
title: "CDRW + DVDR problems."
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by shriphani on 2007-05-31
I was able to play dvds till yesterday night. This morning I put one in and ubuntu reported that it couldn't mount it. The output was something like bad superblock or bad fs type and so on.
I tried to mount the dvd from the command line by typing:
mount /media/cdrom
The out reported that /dev/sdc0 didn't exist. I check Hardware Information and the device was /dev/hdc. I changed it to /dev/hdc in /etc/fstab. I can now mount my dvd. Unfortunately the icon doesn't show up and totem doesn't see it. I tried to point totem to /media/cdrom0 and it plays all the vob* files in a wierd order. I checked Hardware Information again. I could see my dvd drive listed and I could see my dvd there as well.
I have no idea how to proceed. I want to play my dvd's thats all.

---

### Post by shriphani on 2007-05-31
Just to put in some more information.
This occurred while I was running the 2.6.20-16-generic kernel. I am sure that the bus type recognized was IDE. I rebooted to use the 2.6.20-15-generic kernel and now bus type is named SCSI. Apparently there is no device named /dev/hdc ( as reported by mount.)

---

