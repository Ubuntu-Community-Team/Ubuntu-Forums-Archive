---
title: "Transcend StoreJet 1TB EHDD isn't available (but is present at Disks)"
date: 2018-06-01
forum: Hardware
---

### Post by kwak19832 on 2018-06-01
Hi guys, 

I'm "new" to this forum (haven't posted since 2010), so please be gentle!

Because I'm having problems with the above mentioned external Hard Disk Drive Transcend StoreJet 1TB EHDD in both Windows 10 (build 1803) and Ubuntu Ubuntu 18.04 LTS Desktop Edition I'm hoping this forum can provide me with much needed help.
First of all my EHDD worked perfectly on Windows when suddenly I heard the USB disconnecting sound, and I didn't think much of it.
I tried to remove the device and plug it in and it seems to be working fine, but isn't shown as an HDD (E:/) but as a local disk (E:/) and I can't access the disk (not responding).
When I go to Disk Management I see the drive as usual.

In the past I had a similar problem which I could solve by running Ubuntu from a live-CD.
I tried this solution by downloading the latest Ubuntu Desktop Edition (18.04 LTS) and burning it on a DVD.
Booted the live-environment and attached the EHDD to try and open Files, but the EHDD isn't showing.
When I check Disks (see pictures)[IMG]https://www.facebook.com/photo.php?fbid=10156072050931253&set=pcb.10156072051326253&type=3&theater[/IMG], the EHDD is available, with the following info:

[IMG]https://scontent-ams3-1.xx.fbcdn.net/v/t1.0-9/34067447_10156072047951253_2318186191171616768_o.jpg?_nc_cat=0&oh=b34a7109413b0ed7409c47e36856f33f&oe=5BC43131[/IMG]

1.0 TB Hard Disk
Model ST1000LM024 HN-M101MBB (2AR20003)
Size 1.0 TB (1,000,204,886,016 bytes)
Partitioning Unknown ()
Serial Number S2RUJ9AD805743
Assessment Disk is OK, 23 bad sectors (27°C / 81°F)

Any tips to access this drive?

Thanks in advance!

---

### Post by kwak19832 on 2018-09-13
Nobody?

---

### Post by Autodave on 2018-09-13
To me it sounds like the disk has died. Since Linux has no idea about the partitioning, the superblock is probably corrupt. At this point I doubt that you much hope of recovering anything.  Sorry.

---

### Post by kwak19832 on 2018-09-27
> **Autodave said:**
> To me it sounds like the disk has died. Since Linux has no idea about the partitioning, the superblock is probably corrupt. At this point I doubt that you much hope of recovering anything.  Sorry.

Not the answer I was hoping for, but thanks anyway.....

---

