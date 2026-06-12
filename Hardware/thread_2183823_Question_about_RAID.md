---
title: "Question about RAID"
date: 2013-10-26
forum: Hardware
---

### Post by uwe-bungto on 2013-10-26
I have a question about Raid 1 setup. I was thinking of setting up my D-Link NAS as a Raid 1. If sometime in the future this NAS dies can I move the HDD to another NAS or whatever without loosing the data on them?
Paul

---

### Post by TheFu on 2013-10-26
Most proprietary RAID systems use a proprietary disk format that is NOT portable. That happens with other vendors AND with HW-RAID controllers. Even similar models, but different revisions, are known to have different data layouts on HDDs.  

It isn't always this bleak - sometimes they use standard Linux tools and with a little research, you may discover that a specific vendor/model/revision has not modified the software too much.  I think that is the exception, NOT the rule, however.

RAID is not a substitute for backups, so moving HDDs to other RAID subsystem solutions shouldn't be a big deal, provided you have a backup that doesn't fail at that point and can be restored from into the next RAID system.

Does this make sense? Ask if not.

---

### Post by uwe-bungto on 2013-10-27
> **TheFu said:**
> Most proprietary RAID systems use a proprietary disk format that is NOT portable. That happens with other vendors AND with HW-RAID controllers. Even similar models, but different revisions are known to have different data layouts on HDDs.

RAID is not a substitute for backups, so moving HDDs to other RAID subsystem solutions shouldn't be a big deal, provided you have a backup that doesn't fail at that point and can be restored from into the next RAID system.

Does this make sense? Ask if not.

Thanks
If I understand you correctly I should backup any data on the RAID even though it is mirrored; because the next RAID system may not be able to read the HDDs.
What about Software RAID if I had an old box running Ubuntu to act as Network storage? Would this future proof it?

---

### Post by TheFu on 2013-10-27
> **uwe-bungto said:**
> Thanks
If I understand you correctly I should backup any data on the RAID even though it is mirrored; because the next RAID system may not be able to read the HDDs.
What about Software RAID if I had an old box running Ubuntu to act as Network storage? Would this future proof it?

There is no such thing as **future proof**, but I have migrated a software RAID setup through 3 different physical servers. It is still running 10.04, so I don't know if the 12.04 migration will work or not. I'm getting close on the migration date, but can't get a virtual machine to migrate to any other VM-host server here. It is a little frustrating.

RAID1 just means your data can be corrupted quickly in 2 places - at-the-same-time.  RAID is about availability, not backup.  If you don't have excellent, automatic, trusted backups - then you have NO BUSINESS screwing around with RAID, IMHO. Backups can solve 100x more issues than RAID. Maybe 10000x more.  Like a virus or file corruption from software errors.  What good is RAID then? OTOH, with 30+ days of backups, you can restore the corrupted files from before the problem.

With a backup, you can restore and have the system working in a few hours - worst cast. 
With RAID, either there won't be an outage OR is will never come back up due to some other complexity in the system. Backups are still required.

---

### Post by partloer on 2013-10-27
> **TheFu said:**
> I have migrated a software RAID setup through 3 different physical servers. It is still running 10.04, so I don't know if the 12.04 migration will work or not.

What type of servers do you have setup and how do you sync them?

The reason I ask is I am in the planning stages of building a HTPC and I was thinking about RAID 1 to save all of my movies but if that is not effective then I need to come up with another method.

---

### Post by uwe-bungto on 2013-10-27
Thanks.
Now that is cleared up, I think I'll pass on RAID and keep going with the backup system as in the past

---

