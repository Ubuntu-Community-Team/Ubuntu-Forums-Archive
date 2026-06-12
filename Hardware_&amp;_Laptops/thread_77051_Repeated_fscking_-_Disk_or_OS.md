---
title: "Repeated fscking - Disk or OS?"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by Myrios on 2005-10-16
Hi all,

I've been happily running Ubuntu 5.04 for a month or so now, and recently upgraded my hard drive, moving from a 20GB disk to a 200GB disk. I partitioned the new disk so that I had 40GB for the system (which it's unlikely to ever use) and the rest was left for /home (oh, and some Swap space of course).

Three days ago I was working away when all of a sudden applications stopped loading. They would half-load (so that I would see the outline of a window or some such) and then stop. Checking one of the other TTYs showed me that / (/dev/hda1) had been remounted readonly because of errors. I rebooted, but the system refused to boot at all, such were the errors.

I booted using [DSL]("http://www.damnsmalllinux.org") and fscked the drive. It took a while because it was full of errors, but it was finally fixed. I rebooted into Ubuntu again and all was well.

Yesterday it happened again - / got remouted read only. The system booted but it happened again and again, even after I'd forced an automatic fsck on boot. I booted into DSL, fscked manually, problem gone.

Until this morning, same story.

I'm currently in DSL, fscking /dev/hda1 before copying its contents back onto the 20GB drive so that I can use that drive as / and then at least have a bootable system. 

My question is this:

Is this likely to be a disk issue, given that my /home directory so far seems unaffected (I haven't fscked that yet, and I'm not going to until I've backed everything up, but it is set to remount readonly on errors) or is it likely that re-running makefs on the partition in question might solve things?

Thanks in advance folks...

**[Addendum]**

Actually, the first time this happened was whilst performing a kernel update on the 11th of October. Could this have something to do with it?

---

