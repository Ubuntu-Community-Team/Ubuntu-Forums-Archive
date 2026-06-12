---
title: "New server, use hardware RAID 1?"
date: 2008-10-28
forum: Hardware
---

### Post by jeffk on 2008-10-28
Later this week I'll be building an Ubuntu 8.10 server.out of commodity/consumer components. 

While this is admittedly a server for speed on the cheap, when it comes to the RAID question, I'm mostly interested in data durability, and rapid redeployment of the configured server if a component fails.

The motherboard is: GIGABYTE GA-EG45M-DS2H LGA 775 Intel G45

The Chipsets (North Bridge, Intel G45, South Bridge, Intel ICH10R) offer SATA RAID 0/1/5/10, presumably hardware accelerated.

I have two Seagate SATA-3.0 7200 RPM 400GB drives, and don't need very much storage.

The application load is purely web apps (Zope/Plone, Django, etc), and Postgresql databases.

What is the best way to configure the storage? 

a) RAID 1 in the BIOS? I have never used RAID before, except in a few legacy SCSI setups configured on windows servers. 

I wouldn't want to use RAID if Ubuntu required some special awareness of the storages. In the event of drive failure or server move, I'd just want to take the surviving drive and boot from it.

b) The second drive mounted, with chron rsync backups?

---

### Post by nixscripter on 2008-10-28
I would suggest software raid instead. It's quite recoverable and depends less on hardware. Directions are here: [https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

---

### Post by cariboo on 2008-10-28
I have done the same thing with my server check out this:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

to setup raid. My server has been running without a problem, until last night when one the drives went bad, Luckily I have been able to copy all the data to a couple of 160Gb external drives. Once fsck finishes I'll see if I can save the drive.

Jim

---

