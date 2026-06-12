---
title: "Reattach RAID 5 array to new system?  Save all data?"
date: 2013-10-16
forum: Hardware
---

### Post by bretcb on 2013-10-16
I am using Ubuntu 12.04 or 12.10 (sorry, I can't recall which updates I did) desktop.   I have 3 x 3TB drives in a software (mdadm) RAID 5, with a logical volume on top of it, formatted ext3, and containing a crapload of data I would prefer to retain.  I also had a single SSD OS drive, which recently and unceremoniously died.

So, my question is, when my new OS drive arrives, and I install new ubuntu on it, will I be able to see / mount / recover my array?  Any pro-tips on how to do that safely?

Thanks in advance.

---

### Post by TheFu on 2013-10-16
backup everything.  RAID is never a replacement for a good backup.

RAID is only to avoid downtime should a HDD fail.

I have migrated an external RAID5 array setup with mdadm between 3 different systems without any data loss. 8.04, 10.04 - it worked.  Haven't done 12.04 yet.  It has been a few years since the last time, but I think when the array was connected, it was "recognized" automatically. Don't quote me. Definitely backup all the stuff you want/need to retain. I've avoided LVM mixing with RAID since huge data loss with it around 2002.

---

### Post by bretcb on 2013-10-16
> **TheFu said:**
> backup everything.  RAID is never a replacement for a good backup.
I am aware, and I have backups of my important data.  The data stored on the RAID is not critical by any means, though I would still prefer it not vanish.

It appears only to be the system drive (SSD that has been running 24/7 for ~17 months) that has failed.

> **TheFu said:**
> It has been a few years since the last time, but I think when the array was connected, it was "recognized" automatically.  Don't quote me.

That's good news.  (Sorry for having quoted you.)

---

### Post by TheFu on 2013-10-16
> **bretcb said:**
> I am aware, and I have backups of my important data.  The data stored on the RAID is not critical by any means, though I would still prefer it not vanish.

It appears only to be the system drive (SSD that has been running 24/7 for ~17 months) that has failed.



That's good news.  (Sorry for having quoted you.)

LVM makes your setup completely different from mine. Probably want to do a vgexport and have everything under /etc/ available on the new box for reference.  Not to mention having all the UUIDs handy.  I hope you have all that stuff backed up.

---

### Post by bretcb on 2013-10-16
> **TheFu said:**
> LVM makes your setup completely different from mine. Probably want to do a vgexport and have everything under /etc/ available on the new box for reference.  Not to mention having all the UUIDs handy.  I hope you have all that stuff backed up.

Well, I will certainly do that *after* I get the new system drive set up.  I sheepishly admit I hadn't done so previously, and it doesn't appear that I can read anything off that SSD any more.  And, quite frankly, if I had, I'd've probably done something dumb with the backup, like store it on the RAID/LVM ... :redface:

When I built the system, I added LVM on top of the RAID after I was advised by a friend, who works as a Linux administrator, that doing so would give me more flexibility if I later wanted to expand or reconfigure the RAID.  I suppose there poses the problem that, even if the *RAID* is recognized, in order to read my data, the *logical volume* will have to be recognized / rebuilt / recovered first, too.  :-k

---

### Post by TheFu on 2013-10-16
LVM does make things much more flexible, but it also adds some complexity that I'm not in a position to help concerning, especially when RAID is added.

I bet there are great LVM/RAID tutorials out there ... or ask that friend for help who made the suggestion originally.

---

### Post by bretcb on 2013-10-17
> **TheFu said:**
> LVM does make things much more flexible, but it also adds some complexity that I'm not in a position to help concerning, especially when RAID is added.

I bet there are great LVM/RAID tutorials out there ... or ask that friend for help who made the suggestion originally.
I have been exercising my google skills, but a frustratingly large amount of results presume I still have the system drive, and that it's the RAID and/or LVM that has had some sort of failure.  Some useful information, to be sure, and I will be extrapolate that information into something useful for my situation, but I have to do it right the first time, or I could end up with a blank volume.  Hence, I'm hoping to attract the attention of someone who has previously been in my situation, and leverage their knowledge and experience to bolster my lack of confidence in my own ability to figure it out.

The original friend is ... less so now.

---

### Post by SaturnusDJ on 2013-10-20
RAID + LVM is completely transportable. I used a Live CD quite some times to access the data. Information: [http://www.tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html](http://www.tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html)

---

### Post by bretcb on 2013-10-21
> **SaturnusDJ said:**
> RAID + LVM is completely transportable. I used a Live CD quite some times to access the data. Information: [http://www.tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html](http://www.tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html)
Awesome, thank you! That's what I was hoping was the case.  I shall make good use of that info in the next few of days.  My new 10k system drive is en route, and I should be starting to rebuild my system soon.

---

