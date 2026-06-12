---
title: "Installing on 2 SATA drives in RAID 0"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by El_MUERkO on 2005-04-27
Hi,

I was told Ubuntu was a very good free distro of Linux, having used windows almost exclusively since 2000 I thought I'd give it a try but I'm stuck on install.

I'm running an Althon 3200 on an NF2 mobo using 2 * 80gig SATA drives in RAID 0.

The Ubuntu install sees each drive individually rather than raided.

I had hoped to setup a duel boot of Windows and Linux on the machine.

Is this not possible now?

I have alot of data and the install tool scares the hell out of me, I dont want to loose anything pushing the wrong button.

Thanks for any help or advice in advance,

Mark

---

### Post by heimo on 2005-04-27
Raid controllers on many (all?) motherboards are not "real" hardware contollers. They need support from drivers and use CPU to do some of the work. On Linux, it's better to use Linux software raid (without motherboard raid) or real hardware raid with application spesific integrated circiut.. (ASIC) which doesn't require support from operating system / drivers. (such as 3ware cards)

I'd suggest using linux software raid. But I would never dream of doing repartitioning, configuring raid or anything like that on drives that contain data that is not on backups.

This is a forum specialised in all kind of storage technology, lots of people who know incredibly well hard disks, raids, on Windows and Linux. This is the place I would go to ask questions on raids, hard disks and related stuff.
[http://forums.storagereview.net/]("http://forums.storagereview.net/")
[http://www.storagereview.net/]("http://www.storagereview.net/")

---

### Post by El_MUERkO on 2005-04-27
Ok I'll have a look into it, thanks.

If worse comes to worse its a good excuse to get another drive  :cool:

---

### Post by heimo on 2005-04-28
Erhm... I just read the title again. Raid 0. Oh my dear. If you're at all worried about your data, you will not be planning to use raid 0. I somehow misread that to be raid 1, which is what I'm planning to do on my computers.

Raid 0 with two disks doubles the chance of losing data on array. And it doesn't gain so much for most applications. You may get better STR (sustained transfer rate), but you will not be taking the best advantage of your I/O. For some applications this is good, for many, not.

This is a subject you want to keep your eyes and mind open. Don't believe synthetic benchmarks. Really, really consider what's good for you. Ok? :)

raid0 = striping 
raid1 = mirroring

---

### Post by Zensunni on 2005-05-01
This is something I'm currently looking into. Right now, I've got a K8T neo fis2er (best board EVER!) which supports the RAID. Every time I've gone to the firmware raid controller on the mobo and arranged the riad0 setup and then windows just picks it up as one whole disk. However, I can't seem to get ubuntu to see it as one disk. It seems to override the firmware settings, for some reason....

If I come across any revelations, I'll post them.

---

### Post by rengens on 2005-12-08
What about dmraid package? does it work on 64bit ubuntu?
Can SATA Raid 1 be configured as hardware raid?

---

