---
title: "High Load Cycle Count for WD HDD"
date: 2010-09-19
forum: Hardware
---

### Post by bgabga on 2010-09-19
I have a WD Caviar Green HDD (1T). It is normal to have Load Cycle Count about 172000 in only 6 months?
The OS is Ubuntu server; the WD HDD is in raid with a Segate laptop HDD (500GB); the Segate Load Cycle Count is only 11511 in 6 months.
The values are reported by webmin SMART section. I tried to play with "Spin down hard disks when possible" from power management without success. The mini server is running about 7 hours per day.

What can I do?

---

### Post by cascade9 on 2010-09-20
Its not a WD "Advanced Format" Green drive is it? (WD EARS models)

---

### Post by bgabga on 2010-09-20
**Make and model** ATA      WDC WD10EARS-00Y

---

### Post by cascade9 on 2010-09-21
> **bgabga said:**
> **Make and model** ATA      WDC WD10EARS-00Y

So its an EARS model. I'd guess that its got an alignment problem (the EARS models use 4kB sector sizes, not the standard 512B). 

I cant recall what guide I used to align the partitions on the EARS drvie here, I'll try to find it. Heres a link with some info on the issue though- 

[http://www.linuxconfig.org/linux-wd-ears-advanced-format](http://www.linuxconfig.org/linux-wd-ears-advanced-format)

---

### Post by bgabga on 2010-09-22
I found the solution:

Since I have important data on this raid architecture I will do the next:
1) Buy a Segate ST31000520AS.
2) Blame Western Digital on all the Forums.

---

### Post by psusi on 2010-09-22
The Green series has a feature where it automatically unloads the head after 8 seconds of inactivity.  IIRC, they have utility you can download to disable it.

---

### Post by cascade9 on 2010-09-23
> **bgabga said:**
> I found the solution:

Since I have important data on this raid architecture I will do the next:
1) Buy a Segate ST31000520AS.
2) Blame Western Digital on all the Forums.

Oh, dear a green power with RAID. 

AFAIK, all of the hdd manufacturers 'advise' that the 'green' models are 'not suitable for RAID'. They run better in linux 'fake' RAID than they do with 'real RAID, but still...you might be better of getting some HDDs that are actually made to do RAID.

---

### Post by psusi on 2010-09-23
Drives don't know or care if they are in a raid or not.  The problem is that the green drives are designed to unload their heads automatically, which leads to many unloads over time if you keep them mounted.

---

### Post by bgabga on 2010-09-28
Finally I stopped the logs:

chmod -x /usr/sbin/rsyslogd

---

