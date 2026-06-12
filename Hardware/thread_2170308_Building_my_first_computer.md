---
title: "Building my first computer"
date: 2013-08-25
forum: Hardware
---

### Post by cdjoya2 on 2013-08-25
Hi all.

Been here before a long time ago, but with the new SSO thing, I think I may have made a second account by accident. Woops :redface: Anyways...

I've been giving a lot of thought to building my first computer, and recently, I acquired the following items from a friend:

[LIST]
[*]ASUS Crosshair IV Formula motherboard
[*]AMD Phenom II HDT90ZFBK6DGR CPU ([click here]("http://www.cpu-world.com/CPUs/K10/AMD-Phenom%20II%20X6%201090T%20Black%20Edition%20-%20HDT90ZFBK6DGR%20%28HDT90ZFBGRBOX%29.html"))
[*]32 GB (8GBx4) sticks of RAM: by RipJaws
[*]TX750W Power SUpply
[*]Cooler Master V6 CPU fan (don't know which model unfortunately).
[/LIST]

Obviously, I want to build a Linux Machine, however, I don't know what parts would interact well with what I've stated above, let alone Linux. My main goals for this computer is to use it for office work, Internet, and as a media hub in my apartment's network. The only problem is where do I start from here?! I know what parts I need to get, but I need some guidance on choosing the correct ones.

Thoughts are more than welcome!!

---

### Post by TheFu on 2013-08-25
DOn't know anything about those specific parts, but with that CPU and that much RAM, you should definitely use lots of virtual machines ---- like 20 ---- on just the box.  You could run a hosting company on it if you add enough disk storage.

For the things that you've listed, this box is 100x more than you need. It would be sad doing office, internet and media file sharing ... seriously. It would be sad.

---

### Post by d-cosner on 2013-08-25
Go with an NVidea graphics card, the rest of your hardware looks great! Having higher end hardware to me means that you should get many years of service out of your build.

---

### Post by cdjoya2 on 2013-08-30
> **TheFu said:**
> DOn't know anything about those specific parts, but with that CPU and that much RAM, you should definitely use lots of virtual machines ---- like 20 ---- on just the box.  You could run a hosting company on it if you add enough disk storage.

For the things that you've listed, this box is 100x more than you need. It would be sad doing office, internet and media file sharing ... seriously. It would be sad.

I just listed those things at the time of writing. I'm hoping that once I have a full time job, I can get back into gaming - WoW, Steam, and the likes. I also plan on using it for trying out other OS's and flavors of Linux.

> **d-cosner said:**
> Go with an NVidea graphics card, the rest of  your hardware looks great! Having higher end hardware to me means that  you should get many years of service out of your build.

Awesome!! Thanks for the advice! I'm hoping this all works together when I get the stuff ready (aka, when I have the money).

---

### Post by TheFu on 2013-08-30
> **cdjoya2 said:**
> Awesome!! Thanks for the advice! I'm hoping this all works together when I get the stuff ready (aka, when I have the money).

If you need money, sell half the RAM. You'll still have more than 4x RAM than most people and nothing in your list will use it.

I prefer nVidia cards too, but can't recommend any specific model. I don't game and haven't spent more than $50 on a GPU since about 2005. For anything that I run, the $50 GPUs are overkill.

The real advice you need is about HDDs and partitioning to make running lots of different OSes as easy as possible.
* Use GPT partitioning, If you won't run any old Linux or WinXP directly on the hardware. The wikipedia article explains lots. For you and me, GPT means never running out of partitions, having access to more than 2TB of storage, and having redundant copies of the partition table at opposite ends of the physical disk.
* Partitioning - leave room for later. No need to allocate all the storage up front.
** 60G for Windows OS and Apps - NTFS
** 200G for User Data under Windows  - NTFS
** 20G x 5 for different Linux installs.  20G is overkill, but ... 10G usually is not quite enough. Maybe 5x15G is the middle ground?
** 2G for swap or 1.5x your RAM if you plan to use "hibernate" - this swap will be shared by all Linux installs
** 10G-100G for /home ... somewhere around 20G is probably enough.  You can share /home across all the Linux installs too, if you like, but understand that different GUI environments can step on each other, so you might want to setup different userids for each environment that you test ... until you decide.
** 500G-3+TB - /Data   This is for big media files - no programs, just data. Make it NTFS so both Linux and Windows can have easy access to it. Do not allocate all of this up front. It will be nice to be able to increase the size of other partitions by 10G, if you outgrow the initial allocation. If you leave 10G of space free between every partition, you'll have some great flexibility in the future. Just a thought.
* I do not use SSDs. I'm not comfortable with the lifespan of those devices yet. I'm probably overly cautious.
* Whatever disks you buy, make sure you have at least that size available so you can backup stuff.
* Put the swap on a different physical disk from the OS.
* Put your data and /home on a different physical disk from the OS.

If you dno't think you'll have 5 Linuxen installed at once or you plan to use virtualization instead, change the 5x to 2x ... it is always very useful to have storage for 2 versions of Linux on a big box like this. You will still need storage for the VMs, but you can put it anywhere inside a normal Linux partition.

The selection of a Linux file system isn't all that critical - if you don't know or don't care, use ext4.

Of course, these ideas might not fit your needs or budget. I hope that others will chime in with other considerations.

---

### Post by cdjoya2 on 2013-08-31
> **TheFu said:**
> If you need money, sell half the RAM. You'll still have more than 4x RAM than most people and nothing in your list will use it.

I prefer nVidia cards too, but can't recommend any specific model. I don't game and haven't spent more than $50 on a GPU since about 2005. For anything that I run, the $50 GPUs are overkill.

The real advice you need is about HDDs and partitioning to make running lots of different OSes as easy as possible.
* Use GPT partitioning, If you won't run any old Linux or WinXP directly on the hardware. The wikipedia article explains lots. For you and me, GPT means never running out of partitions, having access to more than 2TB of storage, and having redundant copies of the partition table at opposite ends of the physical disk.
* Partitioning - leave room for later. No need to allocate all the storage up front.
** 60G for Windows OS and Apps - NTFS
** 200G for User Data under Windows  - NTFS
** 20G x 5 for different Linux installs.  20G is overkill, but ... 10G usually is not quite enough. Maybe 5x15G is the middle ground?
** 2G for swap or 1.5x your RAM if you plan to use "hibernate" - this swap will be shared by all Linux installs
** 10G-100G for /home ... somewhere around 20G is probably enough.  You can share /home across all the Linux installs too, if you like, but understand that different GUI environments can step on each other, so you might want to setup different userids for each environment that you test ... until you decide.
** 500G-3+TB - /Data   This is for big media files - no programs, just data. Make it NTFS so both Linux and Windows can have easy access to it. Do not allocate all of this up front. It will be nice to be able to increase the size of other partitions by 10G, if you outgrow the initial allocation. If you leave 10G of space free between every partition, you'll have some great flexibility in the future. Just a thought.
* I do not use SSDs. I'm not comfortable with the lifespan of those devices yet. I'm probably overly cautious.
* Whatever disks you buy, make sure you have at least that size available so you can backup stuff.
* Put the swap on a different physical disk from the OS.
* Put your data and /home on a different physical disk from the OS.

If you dno't think you'll have 5 Linuxen installed at once or you plan to use virtualization instead, change the 5x to 2x ... it is always very useful to have storage for 2 versions of Linux on a big box like this. You will still need storage for the VMs, but you can put it anywhere inside a normal Linux partition.

The selection of a Linux file system isn't all that critical - if you don't know or don't care, use ext4.

Of course, these ideas might not fit your needs or budget. I hope that others will chime in with other considerations.

Thank you for the immeasurable advice. I'll definitely keep this handy. As for HDDs, I'll be repurposing my laptop's hard drive (320 GB if I remember correctly) either as an actual disk inside the case, or as a back up. I was thinking of using SSDs but I'm a bit hesitant myself - I like the option of fast boot times, but I'm a patient man. Plus I don't have that much money at the moment.

I do have a question though, regarding cases - I have no idea how to choose those and what is suitable. Do I want a full, mid, mini, or micro tower? I'm guessing I should go with the first two, and with that in mind, I'm considering one of the following:
-[AZZA Solano 1000R Black / Red Japanese SECC Steel/Metal mesh in front MicroATX/ATX/Full ATX Computer Case ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811517006")
-[Rosewill THOR V2 Gaming ATX Full Tower Computer Case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811147053")
-[Rosewill CHALLENGER Black Gaming ATX Mid Tower Computer Case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811147153")

Thoughts?

---

### Post by Yellow Pasque on 2013-08-31
Don't waste money on a full tower unless you have a ton of drives. Tom's Hardware likes the Challenger at that price point, but as they point out, it's not going to be the most quiet (then again, cooling a 1090T with the stock cooler isn't going to be quiet either).

If noise is a factor, consider the Antec Three Hundred: [http://www.newegg.com/Product/Product.aspx?Item=N82E16811129042](http://www.newegg.com/Product/Product.aspx?Item=N82E16811129042)
or the Three Hundred Illusion: [http://www.newegg.com/Product/Product.aspx?Item=N82E16811129066](http://www.newegg.com/Product/Product.aspx?Item=N82E16811129066)

---

### Post by TheFu on 2013-08-31
Laptop HDDs are slow. A fast drive matters. With Linux, you won't be booting very often. I routinely see 60+ days between kernel patches, so at least that long between reboots.

As to cases, that usually turns into a personal preference. I've been using the same cases for 10+ yrs.  $20-$30 on a case is fine. Steel is steel, if the MB fits, all the components fit, you can live with the HDD slots, it is good enough. You might want to buy a quality PSU. I like the seasonics. Quiet, good quality control, plus since I'm not a gamer, I don't need more than 430W. That an issue for people with hot, new, high end GPUs. None of my GPUs ever needed extra power connections. The bus power was enough.  I prefer a quiet PSU. Hate noisy computers.

---

### Post by Yellow Pasque on 2013-08-31
OP already has a good PSU (750W is massive overkill even with something like a GTX660, but that's okay).

As for hard disk, I would start out using the laptop disk, keeping separate partitions for root and data, with the goal of eventually getting an SSD when funds allow and moving the root part to it. 

> $20-$30 on a case is fine. Steel is steel
You generally get what you pay for, so if you don't mind flimsy panels and crappy fans, then maybe I could see really cheaping out on the case.

---

### Post by f-jack on 2013-08-31
The roswill chalenger or the azza personally go with the challenger unless u need alot of drive bays

---

### Post by cdjoya2 on 2013-10-16
Hey all,

After about a month, finally got two jobs so I can start to seriously plan what items I'm getting and when I'm getting them (I'm thinking one part per month). With that said, and with the advice above, this is what I plan on buying in the coming weeks.

Graphics card:
Either The [Galaxy GeForce GT 610 GC 1GB DDR3 PCI Express 2.0 Graphics Card]("http://www.bestbuy.com/site/galaxy-geforce-gt-610-gc-1gb-ddr3-pci-express-2-0-graphics-card/5620358.p?id=1218674048398&skuId=5620358") or the [EVGA GeForce GTX 660 SUPERCLOCKED 2048MB GDDR5 DVI HDMI DP Graphics Card 02G-P4-2662-KR]("http://www.amazon.com/EVGA-GeForce-SUPERCLOCKED-Graphics-02G-P4-2662-KR/dp/B00966IREK")

For the Hard Drives, I'm going to use my laptop drive for now, but I don't know how much longer it will last, considering this drive is about 3 or 4 years old. That said, I do plan on having a separate HDD for my OS, and several drives for my data:
For the OS: [Western Digital WD VelociRaptor WD1500HLHX 150GB 10000 RPM 32MB Cache SATA 6.0Gb/s 3.5"]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136928") 
For data (movies, photos, etc; x2): [Western Digital WD Green WD30EZRX 3TB IntelliPower 64MB Cache SATA 6.0Gb/s 3.5"]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136874")

For the DVD/Blu Ray drive:
[ASUS Black 12X BD-ROM 16X DVD-ROM 48X CD-ROM SATA Internal Blu-ray Drive Model BC-12B1ST/BLK/B/AS - OEM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827135247")

Lastly, for the chassis, I'm still trying to decide what the heck to get... After looking at the above, I'm curious what everyone's thoughts are.

Thanks for your guidance and patience!! :D

---

### Post by Yellow Pasque on 2013-10-16
Why bother with a Raptor over a 128GB SSD?

---

### Post by TheFu on 2013-10-16
> **Temüjin said:**
> Why bother with a Raptor over a 128GB SSD?

Excellent question - even I (cautious on HDD equipment) would get an SSD over a Raptor.  I have a Raptor ... it makes too much noise, so it sits inside the case as a heat sink, unplugged, while a spinning 500G Hitachi does all the work on that machine.  For my needs - I run small business VMs - even a 7200rpm semi-slow HDD is fine.

Regardless, get/allocate a drive just for backups. All drives will fail and it is seldom convenient.  Backups have lots of other uses too - data corruption, virus recovery, post-hacked file validation ... if you don't have backups, you cannot really recover from any of those.

I'm cautious with my data - for me, computing is all about the data, not the hardware.  Perhaps in another year or 2, SSDs will be solid enough to trust with my data.  Even then, backup, backup, backup.

---

### Post by cdjoya2 on 2013-10-16
I didn't know about the Raptor having issues - I'll choose something else then. And yes, I'll have many back ups :)

---

### Post by TheFu on 2013-10-16
> **cdjoya2 said:**
> I didn't know about the Raptor having issues - I'll choose something else then. And yes, I'll have many back ups :)

"Issues?" Not really, but ... 

Raptors are expensive.
Raptors are usually noisy.
SSDs are expensive.
SSDs are silent.

Cheap SSDs have higher failure rates, so get a non-cheap model ... I'd check a few reputable IT equipment blog sites for specific models - Toms Hardware, PC Max-Extreme something like those. The performance of SSDs over any spinning HDD will be huge, even raptors.

IMHO, Raptors don't have much use anymore except for places that need replacement drives.  If you are running a RAID10 with 8-way stripe plus mirroring with raptors and 1 fails, buying a single replacement makes perfect sense.  If running a single mirrored setup (RAID1) and 1 HDD fails, it is time to switch to a RAID1 SSD setup. I'd still use spinning HDDs for backups. No RAID.

---

