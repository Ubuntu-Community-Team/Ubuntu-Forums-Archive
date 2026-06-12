---
title: "Replace Ubuntu Server OS HDD with SSD.... recommended SSD ?"
date: 2021-04-29
forum: Hardware
---

### Post by freeflyjohn on 2021-04-29
I have a Dell PowerEdge T30 fitted with 4 x 4TB WD Red HDD, with one of those HDD running Ubuntu Server 16.04.

Since performing an OS update which required a reboot (I think it updated the kernel), the OS HDD no longer boots.

I can still read the HDD when booting from a live Ubuntu Server USB, so I 'think' the problem is software related rather than a hardware fault with the HDD ?

I would like to repair the OS HDD (I have tried grub update / install but had no luck), but as I have been thinking about upgrading to Ubuntu Server 20.4 LTS I was thinking of swapping the OS HDD for an SSD 1TB.

Would any SSD with the SATA III interface be suitable ?

Such as these...

[https://www.ebuyer.com/989513-samsung-870-qvo-sata-iii-2-5-inch-1tb-ssd-mz-77q1t0bw](https://www.ebuyer.com/989513-samsung-870-qvo-sata-iii-2-5-inch-1tb-ssd-mz-77q1t0bw)

[https://www.ebuyer.com/1139123-samsung-870-evo-1tb-sata-2-5-internal-solid-state-drive-ssd-mz-77e1t0b-eu-mz-77e1t0b-eu](https://www.ebuyer.com/1139123-samsung-870-evo-1tb-sata-2-5-internal-solid-state-drive-ssd-mz-77e1t0b-eu-mz-77e1t0b-eu)

[https://www.ebuyer.com/824750-samsung-860-evo-1tb-ssd-mz-76e1t0b-eu](https://www.ebuyer.com/824750-samsung-860-evo-1tb-ssd-mz-76e1t0b-eu)

[https://www.ebuyer.com/801062-wd-blue-3d-nand-sata-1-tb-internal-ssd-2-5-wds100t2b0a](https://www.ebuyer.com/801062-wd-blue-3d-nand-sata-1-tb-internal-ssd-2-5-wds100t2b0a)

[https://www.ebuyer.com/822479-crucial-mx500-1tb-ssd-ebuyer-ct1000mx500ssd1](https://www.ebuyer.com/822479-crucial-mx500-1tb-ssd-ebuyer-ct1000mx500ssd1)

---

### Post by TheFu on 2021-04-30
Ubuntu Server 16.04 ends shortly.
Move to 18.04 or 20.04 ASAP!

Never try to move OSes using failing/bad hardware. That is asking for disaster. Fix the hardware first, ASAP. Moving from 16.04 --> 20.04 is a fresh install, so buy new storage, do a fresh 20.04 install, see all the differences involved, restore your data and *relevant* settings into the new OS. Expect incompatible settings. This is an opportunity to validate your backup and restore procedures.

Best to ask a separate question about enterprise-class SSDs.

---

### Post by freeflyjohn on 2021-04-30
> **TheFu said:**
> Ubuntu Server 16.04 ends shortly.
Move to 18.04 or 20.04 ASAP!

Never try to move OSes using failing/bad hardware. That is asking for disaster. Fix the hardware first, ASAP. Moving from 16.04 --> 20.04 is a fresh install, so buy new storage, do a fresh 20.04 install, see all the differences involved, restore your data and *relevant* settings into the new OS. Expect incompatible settings. This is an opportunity to validate your backup and restore procedures.

Best to ask a separate question about enterprise-class SSDs.

Thanks The Fu,

I don't have any intention of using the 4TB OS HDD, I want to replace it asap.  I don't know if the HDD is a failing/bad hardware as I can read the drive, it just won't boot since the update.  I don't trust the OS after I broke it (see link below for details of what happened) and I want to upgrade to 20.04 anyway, so now is the best opportunity to upgrade both the drive and the OS.

[https://askubuntu.com/questions/1308079/accidentally-broke-ubuntu-16-04-by-removing-python-3-apache2-and-letsencrypt](https://askubuntu.com/questions/1308079/accidentally-broke-ubuntu-16-04-by-removing-python-3-apache2-and-letsencrypt)

I was hoping if the problem with the HDD is just software, then I could temporarily fix it just to get the server is back up and running (Im missing my Plex Server!), whilst in the meantime I look at changing the drive.

I've never heard of enterprise-class SSDs, I had a quick look and they seem to cost twice the price of a standard SSD.  In which case I might stick with a WD Red HDD, its only a home server running things like Plex, Nextcloud and for data storage and backups etc

So is a standard SSD not suitable for a server OS, it has to be an enterprise-class SSD ?

---

### Post by TheFu on 2021-04-30
Your the person with a T30 "Server", so I made assumptions.  My last HW build was under $400 for so much more machine than a "server" would have allowed.  The last 10+ yrs, "server" is code for noisy, power-wasting, hardware, often with proprietary storage controllers and PSUs.

The main reason I can see to buy a server for home use today would be for remote console via IPMI, but only through a security connection with strong key-based authentication. IPMI connections are notorious for terrible security.

Enterprise class SSDs have more spare cells, so they have longer endurance and seldom fail.  In 2016, I was speaking with an enterprise storage controller vendor who said that failures on enterprise SSDs had removed the need for RAID, they were that good.  He did say that banks probably wouldn't listen and would still insist on RAID10 SSD deployments, but if the system wasn't either responsible for $millions/hr or failure would kill someone, that it wasn't worth it.

I generally buy well respected non-enterprise SSDs with endurance specifications spelled out that meet my needs.  It took 3 failures from cheaper SSDs to learn this. Those failures always provided warnings of impending failure, so I was lucky. Also, I have backup religion, so any storage failure is an inconvenience, not a major data loss event.  A friend had a respected name and model of SSD fail within the first week of ownership. I actually own the same model/brand and haven't had any issues in about 2 yrs.  He got a replacement and I haven't heard anything, so guess it is working fine.  Check the endurance numbers. That's my main advice - and flash the latest firmware onto the SSD before you start using it for anything. Best to do that first.

Don't think I'd use any WD-Red anymore.  They decided to split their "Red" line into 2 very different technologies. Be certain you read up on those BEFORE buying.  Ars Technica has a few stories about "Red" drives.

If you aren't planning to attempt an "upgrade", then wipe away and do a fresh install.  My plex runs on 18.04 server. I'm not prepared for 20.04 server yet. I've also installed jellyfin as a more privacy conscious alternative.  Jellyfin does many things better than Plex, but a few things not as well.  But if you look at all the internet traffic Plex is sending, it is clear they care little about our privacy.  Jellyfin sends ZERO, nothing.  That's something each of us needs to decide the importance about.  If all your media is already in the format your client systems can handle, then miniDLNA would be lighter than both Plex and Jellyfin.  Some of my clients demand transcoded video - they support very limited video and audio codecs.

Wouldn't it be nice if all these issues had simple answers?

---

### Post by freeflyjohn on 2021-05-01
Thanks for your excellent and detailed response TheFu.

My main Plex client runs on an NVidia Shield 4k but I have other Plex clients which the server needs to transcode.

I've read arstechnica about the marketing scam WD Red have pulled (Western Digital adds “Red Plus” branding for non-SMR hard drives)

I bought my WD Red 4TB HDDs years ago, they are the WD40EFRX.

So can you recommend a suitable SSD for my OS drive ?

---

### Post by TheFu on 2021-05-01
I've had a number of WD40EFRX over the years.  4TB was my preferred media storage size for a long time. A few years ago, I moved to 8TB, but kept the partition chunks in 4tb so they'd be able to backup to 4tb HDDs. All my storage decisions revolve around the backup strategy.

For plex, I'm careful to split out the /var/lib/plex* stuff from the OS. It has a dedicated LV, logical volume and media goes on HDDs. My plex system doesn't have any SSD. No need. Every time I think about putting a 500G SSD into that machine, I can't justify the cost. The OS drive is outside my 2 arrays. 1 internal and the other external. Both hold 4 3.5in HDDs.  I've had excellent results from WD-Black HDDs. Those are the ones that come with 5 yr warranties.  Have a few of them spinning here - well beyond 5 yrs. Think 1 must be over 10 yrs and not showing any issues in the SMART report.
```
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Black
Device Model:     WDC WD1001FALS-00J7B0

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  9 Power_On_Hours          0x0032   001   001   000    Old_age   Always       -       96114
```
That's 10 yrs, 11 months, 17 days.

> So can you recommend a suitable SSD for my OS drive ? 
I use Samsung SSDs. 
[B]Tips:
[/B][LIST]
[*]Check the endurance numbers to get the lifetime you want.
[*]Leave 20% of the SSD unused. This will let the internal controller use those areas as over-provisioned storage and drastically increase SSD lifetime.
[*]Qualify SSD storage is all virtually mapped, so regardless of what gets shown to the OS as sector 0 and the last sector of the SSD, that isn't reality.
[*]Beware any SSDs that don't have a warranty based on published endurance TBW numbers. Some cheaper vendors refuse to publish those, even after requesting it.
[/LIST]

---

### Post by freeflyjohn on 2021-05-02
> **TheFu said:**
> 

I use Samsung SSDs. 
[B]Tips:
[/B]
[LIST]
[*]Check the endurance numbers to get the lifetime you want.
[*]Leave 20% of the SSD unused. This will let the internal controller use those areas as over-provisioned storage and drastically increase SSD lifetime.
[*]Qualify SSD storage is all virtually mapped, so regardless of what gets shown to the OS as sector 0 and the last sector of the SSD, that isn't reality.
[*]Beware any SSDs that don't have a warranty based on published endurance TBW numbers. Some cheaper vendors refuse to publish those, even after requesting it.
[/LIST]



Thanks again TheFu

I have been using a Samsung SSD 850 EVO 1TB fitted in my Mac Book Pro for many years without any issues.

So the 'Samsung 870 EVO 1TB' looks to be the best out of the 3 drives I found on ebuyer with an endurance of 2,400 TB and a 5 year warranty...

[https://www.ebuyer.com/1139123-samsung-870-evo-1tb-sata-2-5-internal-solid-state-drive-ssd-mz-77e1t0b-eu-mz-77e1t0b-eu](https://www.ebuyer.com/1139123-samsung-870-evo-1tb-sata-2-5-internal-solid-state-drive-ssd-mz-77e1t0b-eu-mz-77e1t0b-eu)

Specs for the 3 drives are below:

Samsung 860 Evo 1TB
[ATTACH=CONFIG]288412[/ATTACH]

Samsung 870 EVO 1TB
[ATTACH=CONFIG]288413[/ATTACH]

Samsung 870 QVO 1TB
[ATTACH=CONFIG]288414[/ATTACH]

I have no idea what you mean by your other bullet point...


[LIST]
[*]Qualify SSD storage is all virtually mapped, so regardless of what gets shown to the OS as sector 0 and the last sector of the SSD, that isn't reality.
[/LIST]

---

