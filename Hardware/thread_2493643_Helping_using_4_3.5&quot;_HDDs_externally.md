---
title: "Helping using 4 3.5&quot; HDDs externally"
date: 2023-12-20
forum: Hardware
---

### Post by leejenon on 2023-12-20
Hi, I would like to use up to 4 3.5" HDD for films and TV. I don't specifically need a NAS, so I was thinking about a 4 bay external USB enclosure.

Do you have any recommendations?

Thanks, Lee

---

### Post by TheFu on 2023-12-20
First, avoid USB. Choose eSATA or some other screw-based connector like infiniband of you go external.

But .... perhaps you can put the drives internal, which is much easier.

They make relatively cheap drive cages for $25 that hold (4) 3.5" HDDs, but fit into (3) 5.25" drive bays, which are typically part of every midtower case - or tower, if you have that sort of monster.
Here's a link.  [https://www.amazon.com/Stainless-Computer-Driver-Adapter-Bracket/dp/B0CJ3GC791](https://www.amazon.com/Stainless-Computer-Driver-Adapter-Bracket/dp/B0CJ3GC791)  I have one of these and 2 hot-swap models which were about $50, [https://www.rosewill.com/rosewill-rsv-sata-cage-34-hard-disk-drive-cage/p/9SIA072GJ92556](https://www.rosewill.com/rosewill-rsv-sata-cage-34-hard-disk-drive-cage/p/9SIA072GJ92556) , not $70. The replacement hot-swap internal cages I've seen today on Amazon are $150-$250, I'm afraid.  Mine came with a huge fan that typically lasts about a year before starting to fail, so add in another $20 for a Noctua replacement fan (I've done this twice now).  [https://www.reddit.com/r/DataHoarder/comments/13ucyi7/cooling_a_4_bay_drive_cage_fan_replacement/](https://www.reddit.com/r/DataHoarder/comments/13ucyi7/cooling_a_4_bay_drive_cage_fan_replacement/) has links to fans.  I'm very pleased with the Noctua fan - quiet and keeps the drives significantly cooler than the other drives in the system without a fan directly pulling air over them.

If you don't have 4 SATA connectors internal, you can get a cheap or "better" SATA controller that is out-of-the-box supported by Linux with kernel drivers built in for $35-$150.  There's an LSI 2-port SAS controller that will support 8 HDDs with 6Gbps connections.  1 SAS port can support 4 SATA disks, just get a $13 cable.

Sadly, external DAS disk enclosures have gotten very expensive from when I was buying them.  I've had a few over the years.  One from an upstart that didn't realize their prices were 100% lower than the competition - Addonics.  They don't sell to consumers anymore. I need a replacement PSU and a newer SATA-to-Infiniband controller for mine.  Sigh.

The other is a MediaSonic PRObox. [https://www.amazon.com/Mediasonic-PROBOX-SATA-Drive-Enclosure/dp/B09WPPJHSS](https://www.amazon.com/Mediasonic-PROBOX-SATA-Drive-Enclosure/dp/B09WPPJHSS)  I have an older model, but it appears the same stupid mistakes exist in the newer models.  The power button is logical, not physical. If the connection doesn't have power on it for about 3 minutes, the entire enclosure shuts off and will not turn on without a human pressing the power toggle. There's no way to do it remotely.  This makes it suitable only for laptops, but not home servers.

[https://www.amazon.com/Sans-Digital-MobileRAID-MR4UT6G-Hardware/dp/B08SJ9ZF6Z/](https://www.amazon.com/Sans-Digital-MobileRAID-MR4UT6G-Hardware/dp/B08SJ9ZF6Z/) model looks interesting.  Just don't use the built-in RAID stuff, since when these things (any company's) fail, it is very difficult to recover any data. Often, only very specific drive models work with RAID setups like this too.  But if you use JBOD, eSATA and Linux SW-RAID, things become much more flexible.  Of course, don't even think about RAID at all until solid backups are solved and working and tested.

Don't use RAID with USB connections.  The USB storage commands are lacking the commands that SATA, eSATA, SCSI, SAS all support.

Best of all, you can make the system this DAS is connect to your NAS for other systems by setting up NFS and/or CIFS.  For media serving, I do something like this and have Jellyfin as my media server to stream content to silent playback devices in other rooms (HDDs do make noise) and over the internet while traveling.

A few years ago, I wrote an article about this - the parts are outdated, but the other aspects should still apply: [https://blog.jdpfu.com/2007/08/20/Build-Your-Own-RAID-5-Array](https://blog.jdpfu.com/2007/08/20/Build-Your-Own-RAID-5-Array) ... in that article, I setup RAID5. Performance sucked.  I wouldn't do that again without a better disk controller.

---

### Post by leejenon on 2023-12-21
Thank you for your detailed reply. I need to take some time to obsorb it all. 

The background to my question was that I have been given a NiPoGi Mini PC Model: GKV3.

So, I thought I could save some space and swap it for my Fujitsu PC (tower) and use external disks.

I'll be back. :)

Lee

---

