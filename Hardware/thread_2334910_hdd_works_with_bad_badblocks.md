---
title: "hdd works with bad badblocks?"
date: 2016-08-23
forum: Hardware
---

### Post by ubto66 on 2016-08-23
ubuntu 14.04 64bit

On a hdd with no warranty I ran badblocks. It found 4 bad blocks. I installed a system on the hdd without getting error messages. Should you use a hdd with bad blocks? Are bad blocks common on hdds? 
Thank you.

---

### Post by TheFu on 2016-08-23
All HDDs have some bad blocks. The firmware relocates those and swaps in "spare" blocks just for this purpose.  There is an entire science around when disks are failing or not and a forum post isn't sufficient to cover even the highlights. Google is your friend.

The best way that I know to determine if a HDD is failing is to enable SMART (bios and on the disk), then watch the numbers as they change. Sadly, SMART data isn't standardized, so what each number means is open to interpretation for every vendor and even every different model of HDD.  However, if the count of spare blocks is being reduced quickly, then we can say that eventually there won't be any spare blocks and data loss will happen. Sometimes those numbers drop very slowly - over years. Other times those numbers change fast, in just a few minutes.  Compare them from week to week on the same disk. Look for patterns that make you nervous. **smartctl** is the program, but the BIOS and disks must support it.

Of course, what we do know is that all HDDs fail. They tend to fail when we need them NOT to fail - at the most inconvenient time. The only solution I know to combat HDD failures and data loss is to have daily, automatic, backups.  Backups have 1,000+ uses beyond just saving data. There are times when backups help with security, anti-virus, root-kit detection, RAID failures, and lots of other times too.  These forums are full of examples of people asking for help that a backup would have solved. I have backup religion after loosing about 80% of my data back in 2002 due to LVM issues - 100% my fault.

So ... if a HDD causes me any issues at all, I take it out of primary use and relegate it to non-critical use - like the 3rd backup or for transporting files to other locations (i.e. sneaker-net).  The same applies to HDDs that are old - for me, old is over 6 yrs, even if the disk doesn't show any issues. Being old is an issue I'd rather not deal with in a HDD.  Plus my data use expands to where larger HDDs are usually needed by that point anyway.

Anyway, hope this helps and I hope that others will chime in with their ideas and experience. Be certain to read the Backblaze HDD quarterly report. It has changed which drives I'll purchase or not.  For example, I'll never buy a Seagate SATA HDD again. Been burned too many times. The $20 savings just isn't worth the hassles to me anymore.

---

### Post by ubto66 on 2016-08-24
Thanks.

---

### Post by TheFu on 2016-08-24
This morning one of my disk arrays had this to say:
```
This is an automatically generated mail message from mdadm
running on romulus

A Fail event had been detected on md device /dev/md/1.

It could be related to component device /dev/sdd3.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdd3[0](F) sde3[2]
      1943010816 blocks super 1.2 [2/1] [_U]
```

Glad I have backups. Just need to swap in a new HDD and re-sync the array. If anything bad happens, may need to wipe and re-assemble the array, then restore data from a backup.  RAID is never a replacement for backups. The only reason this array exists is because it runs production VMs and a failed disk would bring down 10 VMs that people expect to be available all the time.

So ... as you can see. All HDDs fail, eventually and we don't get to pick when or how.  Spent the morning trying to figure out if this issue was a SATA port, cable, controller or really the HDD. Replacement disk is on the way.

---

### Post by TheFu on 2016-08-24
This morning one of my disk arrays had this to say:
```
This is an automatically generated mail message from mdadm
running on romulus

A Fail event had been detected on md device /dev/md/1.

It could be related to component device /dev/sdd3.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdd3[0](F) sde3[2]
      1943010816 blocks super 1.2 [2/1] [_U]
```

Glad I have backups. Just need to swap in a new HDD and re-sync the array. If anything bad happens, may need to wipe and re-assemble the array, then restore data from a backup.  **RAID is never a replacement for backups**. The only reason this array exists is because it runs production VMs and a failed disk would bring down 10 VMs that people expect to be available all the time.

So ... as you can see. All HDDs fail, eventually and we don't get to pick when or how.  Spent the morning trying to figure out if this issue was a SATA port, cable, controller or really the HDD. Replacement disks are on the way - I always buy 2 HDDs at a time, since there needs to be a backup. The new disks are 4TB (old ones were 2TB). This will let me consolidate storage from 4 disks to 2 - always a win, if the price isn't too high. The disk reported as failed is 2.5 yrs old and has a 3 yr warranty. Warranty disks are usually refurbs and the warranty only lasts until the original time is up (half a year). Yes, I'll return it, but that refurb won't be a primary disk here.

To me, data is much more important than any hardware or software. It is all about the data.

---

