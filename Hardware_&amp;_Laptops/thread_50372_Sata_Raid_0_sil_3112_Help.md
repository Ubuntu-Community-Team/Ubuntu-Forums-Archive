---
title: "Sata Raid 0 sil 3112 Help"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by benqbasic on 2005-07-20
Hey

Ive finaly got linux installed with my sil 3112a sata and two 120gb sata hd in raid0 on REDHAT.

To get redhat installed i downloaded some sil3112 drivers (SiI3x12A- Serial ATA). Then ran the installer with these commands:

Linux nolapic dd               (Or somthing simalar)

The only problem was that the last patition i setup would not partition. so i just made the last partition the swap and installed it without the swap and set that up later.



My question is how do i get Ubuntu installed on my raid 0 sata drives with out formating my windows partitions? 

My main problem is that ubuntu seems to see my to hds as seperate not in raid 0.

Any help would be great.
Thanks

System specs:
Barton 3000+
GA 7n400 pro2 mobo
Albatron 6600GT gfx
2*120gb seagate hd's Using (sil 3x12 onboard controller)
1gb TwinMos Ram

---

### Post by terrie on 2005-07-25
[QUOTE=benqbasic]
My question is how do i get Ubuntu installed on my raid 0 sata drives with out formating my windows partitions? 

My main problem is that ubuntu seems to see my to hds as seperate not in raid 0.
[/QUOTE]

I have the same problem on the same hardware (sil controller). 

As i understand, ubuntu just don't recognize it during the installation?

---

### Post by norman_h on 2005-07-25
[QUOTE=benqbasic]To get redhat installed i downloaded some sil3112 drivers (SiI3x12A- Serial ATA).[/QUOTE]
Do you have a link?

---

### Post by norman_h on 2005-07-25
Ok, I did a bit of a search and I found a [link](http://www.opendrivers.com/driver/219490/silicon-image-sii3x12a-sata-linux-raid-driver-v1.0.0.16-free-download.html)  which looks like it has your drivers.

> This is a pre-compiled kernel that has Silicon Image’s SiI3x12 RAID driver incorporated into it. Please note that until noted otherwise here, this is not an open-source driver and is therefore not officially included in any distribution or public kernel.

It appears to be a precompiled binary with no way to easily incorporate it into an ubuntu install...  the Sil3112 chipset probably uses some technology that is held secret by the manufactures due to non disclosure clauses in a contract somewhere...   :???:  so much for the name of the website...  opendrivers hahaha

I'm stuck with the same chipset...  bummer huh?

---

### Post by benqbasic on 2005-07-26
Well Ive given up anyway and have just brought a new hard drive and broken up my raid ones. 

Sad but true I think that until Silicon Image gets there act together raid is going too be quite hard to impossible(On some systems) to setup.

There is a HOWTO on how to READ raid partitions on this forum: [http://ubuntuforums.org/showthread.php?t=2557&highlight=howto+raid](http://ubuntuforums.org/showthread.php?t=2557&highlight=howto+raid) 

But you have to install linux to a pata drive first. However i could not get it working. I could see the drives through dmraid/mapper but could not mount them.

On Gentoo it might be possible to install striaght onto your raid 0 configuration but I dont have any more time to spend researching it. 
Try the gentoo forums if you are interested.

Tell me if you have made any progress.

Thanks

---

