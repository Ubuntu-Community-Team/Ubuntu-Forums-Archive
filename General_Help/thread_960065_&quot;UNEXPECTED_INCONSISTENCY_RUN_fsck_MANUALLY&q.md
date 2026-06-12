---
title: "&quot;UNEXPECTED INCONSISTENCY RUN fsck MANUALLY&quot;"
date: 2008-10-27
forum: General Help
---

### Post by thousandstars on 2008-10-27
Hi.  I've just signed up on here as it seems I have a problem with my Eee PC running Ubuntu.

Yesterday I had to switch off my PC manually after everything froze.  There was also a sound which was hanging.  When I switched the PC back on Ubuntu checked the drives because of the unclean shutdown, but one of the checks failed and I got a couple of messages:

"UNEXPECTED INCONSISTENCY RUN fsck MANUALLY" and "Please repair the file system manually"

I'm not too great at Linux so I don't really have any idea what to do here.  Some simple guidelines would be useful.  Also, have I caused any (permanent) damage to my system?

I've switched my PC on and off a couple of times since the messages during boot, and everything has loaded as it should normally.  But I get the impression that this is a problem that still needs to be fixed.

Thanks.

---

### Post by livestockPimp on 2008-10-27
If this is coming up at boot and not proceeding you can either press "ctrl + d" and hope it will boot, from here you can run fsck or you will have to enter the root password (this will then dump you to a terminal) and run fsck on your partitions.

To run fsck is simple, from the command prompt type "fsck /dev/sda1" and let it run though. (replace /dev/sda1 with your drives partition you have installed Linux on). you should run this on any partitions Linux mounts at boot. (you can see the partitions linux mounts at boot in the "/etc/fstab" file.

---

### Post by thousandstars on 2008-10-27
OK, when I try that I get the message:

"WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage."

And that sounds pretty dangerous.

---

### Post by livestockPimp on 2008-10-27
are you running "fsck" or e2fsck?

---

### Post by thousandstars on 2008-10-27
Well I just typed "fsck /dev/sda1" as directed.

---

### Post by livestockPimp on 2008-10-27
Ok, been a while since I have done that, just load off a boot CD and run it on all the partitions from there.

---

### Post by livestockPimp on 2008-10-27
oh, hold on the eee pc's dont have optical drives :/
If you dont have a USB CD drive you can boot from then I would suggest making a bootable flash drive, they are pretty easy and there are alot of guides on how to make them.

---

### Post by thousandstars on 2008-10-27
Yeah, using an Eee PC makes things more difficult than normal.  In the end I followed the instructions here:

[http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html)

Nothing needed to be fixed after all.

Thanks for your help though.

---

