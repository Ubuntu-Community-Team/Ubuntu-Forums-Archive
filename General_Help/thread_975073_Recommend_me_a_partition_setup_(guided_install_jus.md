---
title: "Recommend me a partition setup (guided install just doesnt work at all) - 8.10 AMD64"
date: 2008-11-08
forum: General Help
---

### Post by Athiril on 2008-11-08
Im running an ASUS P5N-MX, Q6600, 4GB of DDR2, GTX 260, 300GB Seagate SATA2, 1.2tb RAID0 on onboard nvidia raid controller (2x WD 640GB SATA).

Ubuntu wont see the RAID0, it picks up each drive individually, I dont want to partition the RAID0, it stays as one drive, as NTFS.

I would like to mount it though so I can access the resources and HD video footage I shoot on it.


Installer doesn't work for a guided install... I set the partition size I want as 80GB for Ubuntu to auto-divide into it's partitions etc, but it always ends with an error during the resize... never touches or damages the partition.

GParted resizes the partition absolutely perfect :/

So I would have to resize with GParted and use manual... which is fine by me.

So I would like to set 80GB aside for Ubuntu partitions.

I have nfi what to allocate to what and what filesystem etc.

Can someone give me a good general setup for partitions?


I have to say I don't particularly like the lack of advanced controls in the gui configurations (esp network).. also the help section in Ubuntu is wrong, it refers the network configuration to being in adminstration called network instead of preferences called network configuration and other things etc :/

---

### Post by ad_267 on 2008-11-08
Here's a guide to different partitioning schemes: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I've got no idea how this fits in with raid. The default file system used by Ubuntu is ext3 and you'll also need a swap partition (1.5 to 2 times the size of ram). Many people also like to have /home on a separate partition. A default Ubuntu install is about 4GB, mines using about 10GB at the moment.

I think the discrepancy between the documentation and what you see could be because the documentation is based on previous versions of Ubuntu. What sort of features are you missing in the network setup?

---

### Post by Athiril on 2008-11-08
> **ad_267 said:**
> Here's a guide to different partitioning schemes: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I've got no idea how this fits in with raid. The default file system used by Ubuntu is ext3 and you'll also need a swap partition (1.5 to 2 times the size of ram). Many people also like to have /home on a separate partition. A default Ubuntu install is about 4GB, mines using about 10GB at the moment.

I think the discrepancy between the documentation and what you see could be because the documentation is based on previous versions of Ubuntu. What sort of features are you missing in the network setup?


There's no where (other than command line) that allows me to actually inspect the hardware.

Network doesn't work, it picks up my device fine, ifconfig -eth0 says it there, but i cant get onto my local network even with manual settings (ive made another thread about this in networking sections).

I'm running Wubi now, sending it to my RAID0 (for sheer speed), hoping that it will work and boot off it.

I really want to try out kdenlive and cinelerra (and cinepaint), and some commercial compositing software like nuke or fusion.

Seeing as kdenlive can do HDV firewire capture (firewire doesn't work on Vista x64, the VIA page says they dont and will not write drivers for their own card that I bought (slack bastards!) but Microsoft write a driver... well the driver for the Vista x64 doesnt work :/ lol), so that'd be a step up..

I only have Windows left for Premiere Pro (with After Effects) and Lightroom + Photoshop, the linux software is better than After Effects, so I want to try out these two NLEs, I only need to be able to basic cuts and transitions, everything else can be handled in compositing.


Unfortunately there is absolutely nothing that can compare to Lightroom + Photoshop for real work.. I've got high hopes for Krita in the future.

I've given up on GIMP, apart from the poor UI, even when I tried the new version out on Ubuntu off the live CD the basic fundamentals that make up proper editing are slow as hell (things based on brush work - mostly large soft brushes are slow, healing is horrendously slow even more so), and the lack of 16-bit... 

But yeah I'll keep Windows for my photography, and see if I can get Ubuntu with current software running a good workflow for film.

---

### Post by ad_267 on 2008-11-08
That's weird having issues with the network. Usually it's wireless that's a problem due to hardware support. Wired network connections should work straight away, hope you get that sorted out in the other thread. GIMP probably won't perform very well from a live CD, it should be a lot faster from an actual installation. 16 bit support is also coming with the new GEGL backend which is partly implemented in 2.6, so maybe still keep an eye on GIMP. Another NLE for Linux I've heard is very good is [Piranha]("http://www.ifx.com/products/piranha").

Did the partitioning page explain everything you needed?

---

