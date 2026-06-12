---
title: "Clean install v8 vs. upgrade from v6, partition differences"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by ladasky on 2009-05-16
Hi folks!

I have a desktop x86 box which has been running Ubuntu for a few years.  I started with v6, and eventually upgraded to v8.  I partitioned my hard drive when I installed v6.  At the time I read that it was recommended to have a dedicated disk swap partition, a system partition, and a user partition.  So I did that.  As I upgraded my OS, the underlying structure of my hard disk was left unchanged.
 
I just acquired a laptop onto which I installed v8 directly, without the upgrade history of my desktop machine.  The default configuration of the v8 installation was a single partition spanning my entire hard drive.  I chose that, and everything seems to be working...
 
...but now I would like to know, what is the reason for the change?  Are there benefits and drawbacks to each method?  Since I'm about to put together a new desktop system to replace my old one -- with RAID 1, no less -- I want to know what is the best way to proceed.

---

### Post by zvacet on 2009-05-16
It is possible to have root home and swap in any version of Ubuntu.For that you have to choose manual install method.As you already know benefit is that you can upgrade,reinstall... without losing your data and settings.

---

