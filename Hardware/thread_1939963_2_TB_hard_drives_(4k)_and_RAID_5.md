---
title: "2 TB hard drives (4k) and RAID 5"
date: 2012-03-12
forum: Hardware
---

### Post by zinite on 2012-03-12
I recently converted my home media server from Windows Server 2008 to Ubuntu 11.10 server. Right now, there is a single WD20EARS 2 TB hard drive formatted as NTFS that's about to run out of space.
I'd like to purchase a few extra drives (the case can hold an additional two). I have a few questions before I actually purchase anything though:

The original reason I was running Windows Server was because of the way 4k sector drives are handled on Linux. I've since found [this guide]("http://ubuntuforums.org/showthread.php?t=1600517") that might fix it, but I'm also seeing people say that it didn't work. Which 2 TB hard drives have the best compatibility, and where can I find a guide that will walk me through configuring the special partitioning for these drives (or can I avoid the complications all together?)?

I'll be building the new RAID as ext4, transferring the NTFS drive data, then reformatting that drive and adding it to the RAID.

Am I going about this the wrong way? Not too concerned about performance, just need lots of room for my media collection to grow.

I can navigate my way through tutorials, but I lack the Linux background to jump into this without some help. Setting up and maintaining this server has been quite a learning experience for me.

Running on server:
Crashplan
Sickbeard
Couchpotato
Sabnzbd+
Plex Media Server

---

### Post by zinite on 2012-03-13
Anyone have any recommendations for a RAID with 2 TB hard drives that actually works?

---

### Post by recluce on 2012-03-13
> **zinite said:**
> Anyone have any recommendations for a RAID with 2 TB hard drives that actually works?

The WD20EARS is not a good drive for a hardware RAID, just google "RAID dropouts" and "TLER" to understand that that is the way WD wants it.

In a software RAID, it might behave better - depending on how the RAID handles a temporary dropout of a drive. The ideal solution would be ZFS if you plan to add a couple more drives, but unfortunately that means migrating your server to FreeBSD, as the FUSE-ZFS implementation under Linux is unsafe (may get confused and overwrite other, non zpool/spare drives), buggy and outdated (V23 versus V28 on FreeBSD).

That being said, if you want to use the WD20EARS in a RAID5 setup, please bear in mind:

- This drive works with 4k blocks internally but 512b blocks externally, so you need to align to 4k blocks, similar to SSD alignment. In other words, do not use the first 4k of the drive.

- You really want to disable head off-loading or at least set it to a more reasonable time. As is, the heads are parked after **6 seconds** of inactivity, which can lead to your drive exceeding its Load Cycle design limit in less than a year! Check out "WDIDLE3.EXE" to set this parameter. You need to boot into MS-DOS or FreeDOS **once** to set this parameter.

---

### Post by zinite on 2012-03-14
> **recluce said:**
> The WD20EARS is not a good drive for a hardware RAID, just google "RAID dropouts" and "TLER" to understand that that is the way WD wants it.

In a software RAID, it might behave better - depending on how the RAID handles a temporary dropout of a drive. The ideal solution would be ZFS if you plan to add a couple more drives, but unfortunately that means migrating your server to FreeBSD, as the FUSE-ZFS implementation under Linux is unsafe (may get confused and overwrite other, non zpool/spare drives), buggy and outdated (V23 versus V28 on FreeBSD).

That being said, if you want to use the WD20EARS in a RAID5 setup, please bear in mind:

- This drive works with 4k blocks internally but 512b blocks externally, so you need to align to 4k blocks, similar to SSD alignment. In other words, do not use the first 4k of the drive.

- You really want to disable head off-loading or at least set it to a more reasonable time. As is, the heads are parked after **6 seconds** of inactivity, which can lead to your drive exceeding its Load Cycle design limit in less than a year! Check out "WDIDLE3.EXE" to set this parameter. You need to boot into MS-DOS or FreeDOS **once** to set this parameter.

I remember doing the wdidle3.exe when I first got my WD20EARS. 

How about this: What similarly priced drive can I buy three of to just get rid of the WD all together? Does the Seagate Barracuda 2TB 7200RPM with SmartAlign negate this problem?

---

### Post by recluce on 2012-03-14
> **zinite said:**
> I remember doing the wdidle3.exe when I first got my WD20EARS. 

How about this: What similarly priced drive can I buy three of to just get rid of the WD all together? Does the Seagate Barracuda 2TB 7200RPM with SmartAlign negate this problem?

I have no recent experience with Seagate, because I only use WD here. This is due to personal experience with various HD manufacturers - everbody has different experiences with hard drives, so this is not a statement that one manufacturer is better than the other.

Smartalign sounds like it might prevent alignment issues. However, I would always partition a drive for a RAID5 to prevent size issues. If you set aside about 1% of the drive space, you could avoid issues if you need to replace a drive later on with a different model. If said different model is just one block smaller than the old device, it would not be accepted as a replacement drive in most RAID setups. But since you set aside a bit of space as unused on the older drives, you can create a partition of exactly the right size on the new device, with just the unused space being slightly smaller. Also, if you take care that your partition starts on a 4k boundary, you have just taken care of your alignment problems.

So while I cannot speak for or against the Seagate disk you are eyeballing, I would not mix 7200 rpm drives and 5400 rpm drives in the same RAID. Either buy two 5k drives and use them with your WD20EARS or replace that drive and get three 7K drives.

Prices? Right now, who knows? Due to the Thailand disaster, prices are still highly volatile. But mostly, Seagate and WD price comparable drives allmost the same.

---

