---
title: "Blu-ray player fails to see medium"
date: 2014-07-22
forum: Hardware
---

### Post by Mad_Hadder on 2014-07-22
My blu-ray rw drive started to act up the other day.  I was in the process of copying dvd contents to my hard drive when between two disks the drive quit auto-mounting.  I noticed the automount feature quit detecting the ejection of the disk and would have trouble seeing the next disk after I switched.  I could resolve this by telling the drive to unmount the drive and then eject then re-insert.  This worked for about 2 more disks.  Then the drive quit mounting all together.  Mounting by hand using

sudo mount /dev/sr0 /mnt

only resulted in this error

mount: no medium found on /dev/sr0

I have searched on forumns across the web but haven't gotten any answers that seem to work.  I am currenlty running Ubuntu 13.10. I just upgraded from the previous release as an effort to try and solve the problem with no luck. I know I still need to go up to Ubuntu 14.04 but I am also running with a Xen hypervisior which bogs me down for a few hours after every update on top of normal update time.

Thanks in advance.

---

### Post by Mad_Hadder on 2014-08-07
Update:

My work computer had a similar problem, turned out to be something went wrong with the DVD drive.  It was a windows system, but it could read DVDs just not write them.  I replaced the drive with one from an identical system and it started working.  

The blu-ray drive on my home system is only a few months old.  I would be surprised if it is bad already.  I haven't had any time to try and debug it further unfortunately. If anyone has any ideas please post.  Thanks in Advance.

---

