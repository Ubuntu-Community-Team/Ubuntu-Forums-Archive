---
title: "Relevance of Hard Drive Shutdown"
date: 2022-09-06
forum: Hardware
---

### Post by yayou on 2022-09-06
Hi there,

There are pros and cons of shutting down hard drives when not in use. Some say it increases their longevity and others say it's the opposite. I thought about it because mine easily reaches 50° if I stop my (external) fan for 10 minutes and I was wondering if that could cause even a slight drop in temperature. But with the complexity of today's computers and all the mysterious system operations, is it really possible that nothing is accessing a hard drive for several minutes?

Thanks for reading me.

---

### Post by TheFu on 2022-09-07
Different storage has different features, performance and operational parameters.  If the correct storage is being used for the correct workloads, then things should be good.  If the wrong storage is used with the wrong workloads, things can be really bad.

If there's only 1 storage device in a system and it is a normal server/desktop install without any specific configuration changes to prevent writing stuff like logs periodically, then the drive won't ever stop spinning, but if the device is for data that is seldom used and set to sleep, then a drive that spins down for 23 hrs a day could be smart.

But it all depends on the workload.

I take steps to prevent any HDD storage from spinning down in my systems. I think this works best for my specific workloads.  Most of the HDDs have exceeded their warranty, some are nearly 3x longer than the warrant and still show no issues at all.  But it all depends on the workloads.  I've had a few HDDs fail before the warranty or within a few months of the warranty expiration.  The workload and drive type were not well matched, sadly.  Plus, some drives are just poor for any workloads.

---

### Post by yayou on 2022-09-08
Thank you TheFu. You told what I suspected. Since I only have one Hdd it will always be in demand and will never stop spinning. Now I know why I must forget this idea. Thank you very much for all these good advices.

---

### Post by TheFu on 2022-09-08
> **yayou said:**
> Thank you TheFu. You told what I suspected. Since I only have one Hdd it will always be in demand and will never stop spinning. Now I know why I must forget this idea. Thank you very much for all these good advices.

Seems the first thing you need is a backup drive.
And I'd move any media files to an external USB device. Around here, it is hard to find any smaller than 2TB for $40, so get 2 - a primary and a backup.

---

### Post by yayou on 2022-09-08
Media files in USB device? Except few important text documents, all my data are on external Hdd and some other on the internal one.

---

### Post by TheFu on 2022-09-08
> **yayou said:**
> Media files in USB device? Except few important text documents, all my data are on external Hdd and some other on the internal one.

Current Ubuntu Gnome-based Desktops really need 40G storage, though if you try really hard, it can work great under 20G if you choose a lighter DE, say Lubuntu or Xubuntu. This means NOT installing lots of GUI programs. GUI stuff uses more disk space.  I ran my desktop in 15G of space from 2008-2020 with Ubuntu systems prior to 18.04.  That added about 5G more to the system. When I installed 20.04, I ran into problems with less than 35G.  Just so much bloat.  If you remove and avoid using Snaps, that will probably save 2G-10G of space.  A few programs are only provided as snap packages, so to keep those, you'll need to find a trusted PPA that provides non-snap versions.  In 22.04, firefox and chromium are released as snap packages, but Canonical is pushing more and more that direction.  NOT using snaps was relatively easy pre-20.04, then Canonical started making it harder and harder with each release.  For example, some people remove the snap-package infrastructure and add Mozilla's official PPA under 22.04, only to find that the firefox snap package is listed as a mandatory dependency for some other packages.

---

### Post by yayou on 2022-09-09
You must be right with 40 GB. The minimum requirement for Kubuntu is 25 GB of free space but it's better to go above to work and experiment the system with more freedom.

---

