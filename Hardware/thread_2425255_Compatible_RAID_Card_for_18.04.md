---
title: "Compatible RAID Card for 18.04?"
date: 2019-08-22
forum: Hardware
---

### Post by stickfigure2 on 2019-08-22
I'm really new to Ubuntu. I've been working with an old server based on an ASRock Rack EP2C602 MOBO.
I have been working on this for about 2 weeks.

Here's my issue: I have a High Point Rocket Raid 640L that works fine with Windows but not-so-much Ubuntu. High Point support has been less than helpful. 

Here's my question: Is there a RAID card that supports RAID 5, is as easy to work with as the 640L and works with Ubuntu 18.04 out of the box?

I'm not married to the 640L. I like the ease of set-up under Windows but it isn't critical.
If anyone can recommend a PCIE card with at least 4 ports that I can drop in, install the driver, build a RAID 5 array and get on with my life I would REALLY appreciate the info.

FYI: I did look into finding something that would work but all of the posts I found dated from 2017 and before.

Thanks in advance for any help provided.

---

### Post by lammert-nijhof on 2019-08-22
Can you pass the disks directly to Ubuntu, bypassing or switching off the RAID functionality on the card or is there a disk controller on the motherboard? 
If so you could use a software raid; mdadm or even better the ZFS file system.. ZFS does not support HW Raid Cards, it needs full control of the disks, so any simple disk controller is fine.

I use ZFS and the system is very reliable. ZFS has been developed by Sun in 2005 and now it is Open Source, it is called "OpenZFS" or for Linux "ZFS on Linux". Originally it has been developed as server storage system, but I use it on desktops and laptops without any issue. ZFS is used by Solaris, Linux, FreeNAS, Unix BSD derivatives, Proxmox and others. 

It has the next facilities:
- protection against file corruption through Copy On Write (COW), solved on HW Raid Cards by a battery.
- Raid-0 ,1 ,5 ,6 and 10
- compression LZ4, GZIPx and others
- encryption is supported in ZFS 0.8.1 in Ubuntu 19.10
- snapshots
- incremental backups based on snapshots, locally or over SSH using send/receive, while sending only the modified records.
- memory and SSD caching
- I use it with partitions using disks of different sizes. In Raid-0; I mix 2.5" and 3.5" disks with 320, 500 and 1000 GB.

I started using ZFS for my data and virtual machines, while booting from ext4. But using a simple explanation and around 10 CLI commands I moved Ubuntu to ZFS and now I boot from ZFS too. 
In Ubuntu 19.10 (October) Canonical promised to support installing the system on ZFS and booting from ZFS.

---

### Post by TheFu on 2019-08-22
I've been burned by HiPoint too.

In a business, using a HW-RAID can make sense, provided you have a spare onsite for when it fails.
In general, $400+ LSI RAID is the brand to use unless you have a Dell, HP or IBM server, then you'd use one of their branded cards (which is probably an LSI underneath). Make sure the batteries are ok on the RAID card.

For a home setup or for a small business, most Linux installs use SW-RAID which is managed using either LVM or ZFS or mdadm.  SW-RAID is 1000x more flexible than HW-RAID and on any recent (last 10 yrs) HW, it is just as fast, sometimes faster.  With Ubuntu, RAID is for the data storage, not the boot or OS. I haven't looked closely at 18.04 or later releases, but they did rework the installation program, so perhaps install onto SW-RAID is trivial in Ubuntu now?  RHEL and CentOS always handled that better previously. I setup SW-RAID on a CentOS machine during the installation around 2010 and it was easy.  SW-RAID accesses the disks in using JBOD.

Using ZFS for data storage (non-OS) is supported. ZFS is pretty awesome.  Using it for boot or OS on Ubuntu is considered beta and is a technology preview for now. Expect some issues for now.  Keep your server on 18.04, like you plan.  Servers shouldn't be using non-LTS releases without very good reasons.  The data is more important than the hardware, right?

The main problems with all HW-RAID is that the data is tied to that specific card sub-model. A newer model can often not access data stored using an older version of the card. The only solution for that problem is to flush all the data, rebuild the array and reload the data from backups.

---

### Post by stickfigure2 on 2019-08-22
[**[COLOR=#000000]lammert-nijhof[/COLOR]**]("https://ubuntuforums.org/member.php?u=1949495") 	 

Thanks for the info. 
I prefer a hardware solution. This is for my small business and buying 2 cards is not an issue.
My experience with software solutions has been that rebuild times after a disk failure can take forever whereas hardware solutions tend to be fairly quick.
That said, if I can't find something that works sounds like ZFS might be a good compromise.

---

### Post by stickfigure2 on 2019-08-22
[URL="https://ubuntuforums.org/member.php?u=1037685"][B][COLOR=#000000]TheFu
[/COLOR][/B][/URL]
Thanks for your reply. The RAID is for data storage only. The machine boots from an SSD.
About an hour after I posted I found LSI and will spend tomorrow looking hard at their products.
I stumbled on them as a result of yet another Google search that produced an Ubuntu Certification page for RAID controllers. [https://certification.ubuntu.com/catalog/category/RAID/](https://certification.ubuntu.com/catalog/category/RAID/)
Thanks again for your reply and your advice.

---

### Post by 1clue on 2019-08-22
+1 for what TheFu said.

There is a lot of supporting evidence suggesting that software RAID is actually better than hardware RAID. That's not to say that a really good RAID card isn't better, but I can assert that anything less than a really good RAID card (plus a spare) is going to lose out to software RAID.

The thing you already know is that if your card fails or stops being supported by your host OS, you're pretty much out of luck with hardware RAID. If your RAID card flakes out and you don't have a spare, you're out of luck. If the spare isn't exactly the same version as the original, you could very well be out of luck.

Software RAID, well you need some sort of Linux box, and some way to hook the drives you have to that Linux box. So you could use a native SATA interface on the original host, then when you're trying to pull your system back together after a crash you might have to use a USB to SATA converter for some reason. For example, you're using a laptop because everything else was hooked up to the wall and you got hit by lightning, and you REALLY need that data. No problem. 

Dead SATA card? Went from motherboard built-in card to external? One external to another? No problem.

Performance of software RAID is comparable to using hardware RAID on comparable equipment. If you have a nice RAID card that can work as a non-RAID card, you'll get very close performance using either method.

So my recommendation is to find some reputable group who did some benchmarks, read up on their tests and their results. Don't take our word for it. The only thing I'm asking you to take my word on is that it's worth researching before you buy your equipment.

---

### Post by TheFu on 2019-08-23
If you have to install the driver for any storage device on Linux, then you probably want to avoid that device.  Drivers should be included with the kernel. This applies to almost all hardware you want to use on Linux.  If the drivers aren't included and the device is over 1 yr old, skip it or be prepared for pain with every major kernel update.  There was 1 exception to that until about 2 months ago - that exception was GPUs.  Now Ubuntu has access to provide Intel, AMD and nvidia drivers for LTS releases.  Do not go out and get the drivers directly from any of those vendors unless you need the alpha-level versions.
  The Linux software ecosystem is not like Windows.  Completely different overall philosophies.

Only old posts were found because very few people still use HW RAID on Linux.  Very few use "Fake-RAID" anymore either. FakeRAID is what most cheap cards and motherboard-provided RAID solutions provide.  All the RAID work is performed by the CPU like happens with SW-RAID, but the storage access is still tied to some hardware that, if replaced, likely won't be compatible.  There's something about moving an external SW-RAID array between 4 completely different systems and not having any issues that is pretty awesome.

With SW-RAID, you can tune the RAID rebuild to be as slow as you need not to impact current transaction rates
 or
as fast as the hardware can support. Completely up to you.

Suppose that you've read about issues with RAID5 on disks over 1TB in size?  For larger disks, RAID6 or RAIDz2 is recommended, if you can't do RAID1 or RAID10.  When I switched to larger disks from 320GB, the switch to RAID1 was required.  It is all about the safety of the data.  Of course, we have excellent automatic, daily, versioned, "pulled" backups too.  RAID is for HA, nothing else.

---

### Post by stickfigure2 on 2019-08-23
> **1clue said:**
> +1 for what TheFu said.

There is a lot of supporting evidence suggesting that software RAID is actually better than hardware RAID. That's not to say that a really good RAID card isn't better, but I can assert that anything less than a really good RAID card (plus a spare) is going to lose out to software RAID.

The thing you already know is that if your card fails or stops being supported by your host OS, you're pretty much out of luck with hardware RAID. If your RAID card flakes out and you don't have a spare, you're out of luck. If the spare isn't exactly the same version as the original, you could very well be out of luck.

Software RAID, well you need some sort of Linux box, and some way to hook the drives you have to that Linux box. So you could use a native SATA interface on the original host, then when you're trying to pull your system back together after a crash you might have to use a USB to SATA converter for some reason. For example, you're using a laptop because everything else was hooked up to the wall and you got hit by lightning, and you REALLY need that data. No problem. 

Dead SATA card? Went from motherboard built-in card to external? One external to another? No problem.

Performance of software RAID is comparable to using hardware RAID on comparable equipment. If you have a nice RAID card that can work as a non-RAID card, you'll get very close performance using either method.

So my recommendation is to find some reputable group who did some benchmarks, read up on their tests and their results. Don't take our word for it. The only thing I'm asking you to take my word on is that it's worth researching before you buy your equipment.

>> Thanks 1clue. Good information and it looks like the LSI MegaRAID 9361-8i is what I've been looking for. 8 ports, under $400 and lots of support, compatible with 18.04 and enough reviews and bench mark tests to show it's reliable and has a fairly low failure rate. In my case I think it's a history of really bad experiences with SW-RAID and nothing but good results with HW-RAID. That said the 2 RAID arrays that I currently have in service have been running for years without a problem, other than the occasional drive failure, and get incrementally backed up every evening. RAIDs aint for back-up.

Even with all that the information and advice that you and TheFu have provided have led me to take a look at a SW-RAID solution.
thanks again.

---

### Post by stickfigure2 on 2019-08-23
> **TheFu said:**
> If you have to install the driver for any storage device on Linux, then you probably want to avoid that device.  Drivers should be included with the kernel. This applies to almost all hardware you want to use on Linux.  If the drivers aren't included and the device is over 1 yr old, skip it or be prepared for pain with every major kernel update.  There was 1 exception to that until about 2 months ago - that exception was GPUs.  Now Ubuntu has access to provide Intel, AMD and nvidia drivers for LTS releases.  Do not go out and get the drivers directly from any of those vendors unless you need the alpha-level versions.
  The Linux software ecosystem is not like Windows.  Completely different overall philosophies.

Only old posts were found because very few people still use HW RAID on Linux.  Very few use "Fake-RAID" anymore either. FakeRAID is what most cheap cards and motherboard-provided RAID solutions provide.  All the RAID work is performed by the CPU like happens with SW-RAID, but the storage access is still tied to some hardware that, if replaced, likely won't be compatible.  There's something about moving an external SW-RAID array between 4 completely different systems and not having any issues that is pretty awesome.

With SW-RAID, you can tune the RAID rebuild to be as slow as you need not to impact current transaction rates
 or
as fast as the hardware can support. Completely up to you.

Suppose that you've read about issues with RAID5 on disks over 1TB in size?  For larger disks, RAID6 or RAIDz2 is recommended, if you can't do RAID1 or RAID10.  When I switched to larger disks from 320GB, the switch to RAID1 was required.  It is all about the safety of the data.  Of course, we have excellent automatic, daily, versioned, "pulled" backups too.  RAID is for HA, nothing else.

Interesting. Nope. Didn't know about the disk size issue and I will look into it. 
Please take a look at my reply to 1clue. I list the card I'm looking to buy and, thanks to you two, will spend some time playing with a SW-RAID solution.
thanks again.
I

---

### Post by SeijiSensei on 2019-08-23
Linux has native drivers for cards that use the LSI Logic "Megaraid" chipset.

[https://www.newegg.com/p/pl?N=100007607%2050001833%204814&Manufactory=1833](https://www.newegg.com/p/pl?N=100007607%2050001833%204814&Manufactory=1833)

Driver at /usr/lib/modules/5.0.0-25-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko

That said, I also use software RAID via mdadm.

---

### Post by 1clue on 2019-08-23
> **stickfigure2 said:**
> ... and get incrementally backed up every evening. RAIDs aint for back-up....

I see you actually know something about RAID. Good deal.

I'm not going to hound you, and while I don't want to put words into his mouth, probably TheFu won't either. The software solution is worth serious consideration, is all either of us have been getting at. 

None of this matters much when everything is working fine. The only consideration is what happens when it all comes apart. Do what you need to do, and you know your skills and circumstances better than anyone here.

Good luck, have fun and please let us know what you choose to do.

Thanks.

---

### Post by stickfigure2 on 2019-08-23
> **SeijiSensei said:**
> Linux has native drivers for cards that use the LSI Logic "Megaraid" chipset.

[https://www.newegg.com/p/pl?N=100007607%2050001833%204814&Manufactory=1833](https://www.newegg.com/p/pl?N=100007607%2050001833%204814&Manufactory=1833)

Driver at /usr/lib/modules/5.0.0-25-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko

That said, I also use software RAID via mdadm.


Thanks much for the info.
Heading out for the weekend.
When I return I plan to play around with 'mdadm'.
Seems to be a 'go-to' for SW-RAID solution.
Cheers.

---

### Post by lammert-nijhof on 2019-08-27
I would go for ZFS, mdadm does not give you the same level of protection as a HW Raid and ZFS gives you better protection than a HW Raid. See the next complemented excerpt out of Wikipedia:
 
Examples of features specific to ZFS include: 
 
[LIST]
[*]Hierarchical [checksumming]("https://en.wikipedia.org/wiki/Checksum") of all data and [metadata]("https://en.wikipedia.org/wiki/Metadata"),  ensuring that the entire storage system can be verified on use, and  confirmed to be correctly stored, or remedied if corrupt. Checksums are  stored with a block's parent block,  rather than with the block itself. This contrasts with many file  systems where checksums (if held) are stored with the data so that if  the data is lost or corrupt, the checksum is also likely to be lost or  incorrect. 
[*]Can store a user-specified number of additional copies of data or metadata, or  selected types of data, to improve the ability to recover from data  corruption of important files and structures. I have two copies on two different disks for one of my datasets(folders) in my Raid-0 storage. 
[*]Automatic rollback of recent changes to the file system and data, in  some circumstances, in the event of an error or inconsistency. 
[*]Automated and (usually) silent self-healing of data inconsistencies  and write failure when detected, for all errors where the data is  capable of reconstruction. Data can be reconstructed using all of the  following: error detection and correction checksums stored in each  block's parent block; multiple copies of data (including checksums) held  on the disk; write intentions logged on the SLOG (ZIL) for writes that  should have occurred but did not occur (after a power failure); parity  data from RAID/RAIDZ disks and volumes; copies of data from mirrored  disks and volumes. 
[*]Native handling of standard RAID levels and additional ZFS RAID layouts ("[RAIDZ]("https://en.wikipedia.org/wiki/RAIDZ")").  The RAIDZ levels stripe data across only the disks required, for  efficiency (many RAID systems stripe indiscriminately across all  devices), and checksumming allows rebuilding of inconsistent or  corrupted data to be minimized to those blocks with defects; 
[*]Using free memory for caching of disk IO, hit rate often exceeds 80%. The memory will be freed again, if needed for e.g. programs. If you prefer; ZFS supports a minimum and maximum for memory caching size. 
[*]Native handling of tiered storage and caching devices; I use memory caching 4GB, SSD caching 50GB and HDD storage. On a desktop I see 93% hit rates for the memory cache and less than 5% for the SSD cache. The SSD cache only works for booting virtual machines and during initial program loads in those VMs, afterwards the memory cache takes over. In those VMs I have instantaneous response times, since they run from memory cache. For servers it might be different, often they use larger memory caches. 
[*]Native handling of snapshots and backup/[replication]("https://en.wikipedia.org/wiki/Replication_(computing)")  which can be made efficient by integrating the volume and file  handling. I incrementally backup a 64-bits Linux system to a 32-bits FreeBSD system and only the changed records will be sent. In general it will maintain compression through the whole chain to the other disk or other server on the network. 
[*]Native [data compression]("https://en.wikipedia.org/wiki/Data_compression") like LZ4 and other compression algorithms. NOTE: that LZ4 compression almost doubles your effective cache sizes and almost halves the number of disk IOs. 
[*]Efficient rebuilding of RAID arrays &#8212; a RAID controller often has to  rebuild an entire disk, but ZFS can combine disk and file knowledge to  limit any rebuilding to data which is actually missing or corrupt,  greatly speeding up rebuilding; 
[*]Unaffected by  RAID hardware changes which affect many other  systems. Easy to import the storage in another system, just "zpool import <name>" 
[/LIST]
Since ZFS is new for you, I would try out, the new set up in Virtualbox. It will be easy, you only have to think a little bit about the ~5 properties you might want to change from the defaults and such a small prototype is nice to get a feel for the ease of ZFS administration.

---

### Post by stickfigure2 on 2019-08-27
From[**[COLOR=#000000] lammert-nijhof[/COLOR]**]("https://ubuntuforums.org/member.php?u=1949495")      "I would go for ZFS, mdadm does not give you the same level of protection as a HW Raid and ZFS gives you better protection than a HW Raid."

Thanks!
I played around with mdadm a bit yesterday and when I finish checking it out I'll check out ZFS.
I've decided to spend a few weeks rather than a few days working on this. There's no rush to bring up the machine I'm working on and this decision is too critical.

Whatever I do I'll post my decision and why I made the decision.

Thanks to you and everyone who has helped with this!

---

### Post by lammert-nijhof on 2019-08-29
A wise decision!

---

### Post by stickfigure2 on 2019-08-29
> **lammert-nijhof said:**
> A wise decision!

Thanks....... :)

---

### Post by stickfigure2 on 2019-11-04
Hi Folks,

Well 'a few weeks' turned into 2 months. With other things going on staying focused became a problem.
In any event I ended up going with the MegaRAID 9361-8i x 2. For the simple reason that it was just easier.
I picked up the first card, installed it, connected 8 x 2Tb drives and within less than an hour I set up a 6 disk RAID 6 with 2 hot spares.
I picked up a second card and installed it in a test-bench box with another 8 drives and was able to configure a 5 disk RAID 5 with 1 hot spare and configure 2 JBOD drives all on the same card.

While mdadm and ZFS seemed like good solutions the reality was I simply don't have the Linux / C knowledge to become comfortable with either one.

Thanks again to all who contributed. I really appreciated your input and support.

Hope you all have a Happy and Safe Thanksgiving and a Merry Christmas!

Cheers.

---

