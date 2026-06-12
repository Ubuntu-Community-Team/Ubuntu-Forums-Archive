---
title: "bad sectors remapping"
date: 2011-08-31
forum: Hardware
---

### Post by gpost3 on 2011-08-31
Hi,

Bad sectors as well all know are sectors on hard drive that cannot be written to (due to possibly physical damage). Now I know there are Linux tools such as badblocks and chkdsk on windows. 

Question: If I run chkdsk /B on entire disk in windows - will those sectors get marked as "bad" under ubuntu as well? My understanding is that the data that specifies where those bad sectors are located is written in partition table so that the file system knows not to use those bad sectors. My intuition says that say if i run badblocks on ubuntu and mark those sectors as bad - windows won't know about this until i mark those very same sectors as bad again using chkdsk because the partition table for ubuntu is different from the partition table of windows?

Anyone has any certain knowledge on how this works?

---

### Post by Grenage on 2011-08-31
I was under the impression that the drives themselves now identify and mark unreliable sectors.  If I have a drive that keeps generating them, I'll replace it.

---

### Post by gpost3 on 2011-08-31
I used to think that hard drive's SMART feature keeps track of it as SMART does know about bad sector's existence. But I am yet surprised that one of my disk that has a pending bad sector (a sector that hasn't been remapped yet due to insufficient sparse area) still shows under chkdsk as having 0 KB in bad sectors. Yet the SMART does know about its existence and so does Ubuntu. This is basically what confuses me. Unless windows 7 is just plain stupid dumb ***.

---

### Post by Grenage on 2011-08-31
> **gpost3 said:**
> I used to think that hard drive's SMART feature keeps track of it as SMART does know about bad sector's existence. But I am yet surprised that one of my disk that has a pending bad sector (a sector that hasn't been remapped yet to insufficient sparse area) still shows under chkdsk as having 0 KB in bad sectors. Yet the SMART does know about its existence and so does Ubuntu. This is basically what confuses me. Unless windows 7 is just plain stupid dumb ***.

I don't know what '*insufficient sparse area*' really means, but are you really talking about a single bad sector?  Where is Ubuntu reporting the problem, because I believe Ubuntu also uses SMART readings to indicate problems.

---

### Post by gpost3 on 2011-08-31
That is right Ubuntu does indeed use SMART in Disk Utility for this. But to my knowledge, hard drive manufacturers have a sparse area on the disk to reallocate/remap any bad sectors to this new area. I will post back later today with full screenshots of disk utility on my Hitachi drive and compare it to chkdsk on windows to show what I mean. :)

---

### Post by Grenage on 2011-08-31
> **gpost3 said:**
> That is right Ubuntu does indeed use SMART in Disk Utility for this. But to my knowledge, hard drive manufacturers have a sparse area on the disk to reallocate/remap any bad sectors to this new area. I will post back later today with full screenshots of disk utility on my Hitachi drive and compare it to chkdsk on windows to show what I mean. :)

Correct; hard drives are manufactured with an extra area for specifically that task.

---

### Post by trundlenut on 2011-08-31
Normally if the drive has run out of spare sectors to substitute for the bad ones the disk is living on borrowed time.

I would look to replace it ASAP.

---

### Post by gpost3 on 2011-09-01
To be honest I am not at all concerned about bad sectors themselves. I have had this hitachi for over 7 years now - has bad sectors but doesn't have any spin retry errors like one of my seagate has which sometimes fails to be recognized in windows 7. According to my experience with hdds bad sectors is not a good indication of when you should replace the drive unless the bad sectors grow on a weekly basis as Grenage pointed out. Anyway I ran chkdsk on Windows and it reported 0 KB in bad sectors initially. So I ran the chkdsk with /B flag and now it shows 4 KB in bad sectors which makes more sense. It seems to me that windows doesn't use SMART to figure out that there are bad sectors in the disk. The user must run chkdsk /B to reevaluate the bad sectors whereas Ubuntu knows how to deal with it without running badblocks. Another -1 for windows 7.

---

