---
title: "Thoughts on preemptive storage replacement"
date: 2023-06-17
forum: Hardware
---

### Post by aljames2 on 2023-06-17
Replacing currently working HDDs that are beyond warranty by double years.  I am interested in hearing perspectives in when & how people handle these decisions, economics aside.  And then, repurposing the old drives, or disposal methods.

2 prospects for replacement in my setup are two 3TB WD Reds.

---

### Post by TheFu on 2023-06-17
I'd avoid odd size disks - 3TB, 5TB, 6TB are "odd sized".  Go with 4, 8, 10TB sizes for better durability.  Check the Backblaze reports.

When I had a large income, pre-buying storage before there were failures was a way of life.  I'd migrate drives off primary storage to backup storage when the warranty period was up.  
After I left the well-paying job (it was killing me), I'd buy a new HDD only when 1 failed or I was seeing some issues in the SMART data that showed it was struggling. Since around 2008, I've had excellent backups, so a single disk failure is an inconvenience, not data loss.  Prior to that, I had a number of disk failures which lost data and it wasn't the end of the world.  I don't even recall what I lost now - just that it was 80% of all the data I had.

I found that drives with less than 5 yr warranties usually disappointed with the length of time they survived. I always felt ripped off.  All HDDs fail, just like we are all going to die, but I'd like for them to fail over 12+ yrs of problem-free service.  When a drive with a 3 yr warranty fails just entering the 4th year, I feel ripped off.  Same for a Seagate with a 1 yr warranty that fails in 13 months or 11 months (had 2 failures with them in the last 10 yrs).  I have some 320G and 300G Seagate drives that are 15 yrs old now.  They don't make them like that anymore and haven't in 15+ yrs.  That is clear.  I don't plan to ever give Seagate another dime.  Also had 2 Hitachi and 5 WD drives fail before I'd have liked, but they all exceeded the warranty.  Only the some WD RED (pre- WD crap with 2 different types of Red designs) and BLACK and Hitachi GOLD HDDs have lasted to the point that I feel they were excellent values.  I've never had a WD-Black fail.  Not one.  There's an old 1TB Black drive that is just starting to show issues in the SMART data now. It is in a system to be retired, so I'm not really in any hurry to replace it.  The 8 drives connected to that system all need to be replaced due to age.  The system and drives are all from 2011.

In a business, I'd replace the drives when the warranty ends.  It is a good driver to get management used to thinking about system maintenance every 3-5 yrs.  At one client, we replaced 22 servers for 2 newer servers and virtualization, which cleaned out their "data center" (a small room that was packed with equipment), reduced their need for a $25K UPS to a $2K UPS, and saved on HVAC costs, while getting all their old, loud, slow, storage under warranty again.  When they sold the old UPS unit used, I think it paid for all the new systems.  That same client thought they'd been doing backups perfectly, but nobody had validated them or even looked at the backup logs.  For over a year, all their backups were corrupted.  They'd been lucky.  Had they needed some of those backups, it was likely the business would have died after a server disk failure.  They weren't using any RAID at all.
For this client, the only thing I didn't really like with our solution was the backups for the virtual machines.  It was ugly, inefficient, took far too long and still the software cost was over $1000.  In the enterprise world, that's nothing, but I'd have rather been able to use F/LOSS instead.  Sadly, they were a MSFT-shop and we'd deployed VMware ESXi + vSphere because at the time, nobody got fired for using VMware.  We did get them a NAS box that was cheap and capable for all their shared storage.  The next year, that same NAS cost 4x more - NAS prices went crazy - because the market would accept the higher prices, not because anything was more expensive or better.

These days, I'd deploy TrueNAS on a whitebox for storage in a business server room. Each server would have 1 or 2 SSDs internal and all other storage would be iSCSI from the TrueNAS.
At a home, things are different. Cheap and multi-use systems are usually needed.

---

### Post by aljames2 on 2023-06-17
> **TheFu said:**
> I'd avoid odd size disks - 3TB, 5TB, 6TB are "odd sized".  Go with 4, 8, 10TB sizes for better durability.  Check the Backblaze reports.

I found a pretty good price on 4TB blacks.  Two of those should do me for now replacing the 3TBs.  I don’t have a ton of data, at 4TB I’m using just under 50% storage.  The 2nd drive is a mirror of the other, not RAID.

> **TheFu said:**
> …..Since around 2008, I've had excellent backups, so a single disk failure is an inconvenience, not data loss. 

Ahh, this does make a good case for not fearing a drive failure & invites the idea of staying the course, see just how long they will last.

---

### Post by VMC on 2023-06-17
I never looked at the expired date. I just used it until the end. I've always had extras and backups of course. A couple  of years ago I replaced my HD with SSD. The speed difference was enough for me to never look back. I now use the HD for backups and/or movies, etc

---

### Post by TheFu on 2023-06-18
> **aljames2 said:**
> I found a pretty good price on 4TB blacks.  Two of those should do me for now replacing the 3TBs.  I don’t have a ton of data, at 4TB I’m using just under 50% storage.  The 2nd drive is a mirror of the other, not RAID.

I use RAID1 for HA and I use delayed copies for less important data that is too large to have proper versioned backups, effectively, media files.

> **aljames2 said:**
> 
Ahh, this does make a good case for not fearing a drive failure & invites the idea of staying the course, see just how long they will last.

For a home, this is fine, probably. YMMV.
In a business, this is completely unacceptable.

---

