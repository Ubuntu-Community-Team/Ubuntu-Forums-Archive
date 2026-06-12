---
title: "Dell E1405 high load average"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by entellus on 2006-07-28
Information using _top_ shows the load average for the last one minute hovering around ~0.5 and often reaches 1.3. The system and configuration I am currently running is as follows:

System:
Intel Core Duo T2400
Intel Integrated 950GMA
1G shared RAM(2x512M modules)

Config:
Fresh Dapper 6.06 Xubuntu install
2.6.15-xx-686-smp kernel
915resolution package

I've already tried the following without being able to resolve the problem:
Switching back to using the 386 kernel
Changing max_cstate to 3 (was 8 originally)
Diabling 915resolution

---

### Post by el3ktro on 2006-09-08
Hello,

I have the same hardware and the same problem on a fresh Ubuntu install. Where you able to resolve the problem? Gnome-system-monitor shows a load of ~50% on both CPUs, while top doesn't show me which process needs so much CPU, so I think it must be a kernel module or something causing this - something which is not shown in the top process list.

---

### Post by entellus on 2006-09-13
> **el3ktro said:**
> Hello,

I have the same hardware and the same problem on a fresh Ubuntu install. Where you able to resolve the problem? Gnome-system-monitor shows a load of ~50% on both CPUs, while top doesn't show me which process needs so much CPU, so I think it must be a kernel module or something causing this - something which is not shown in the top process list.

Sorry, but I ended up switching distros - Arch Linux. It's worked fine for me. If you do find out what is causing this, please do post.

---

### Post by el3ktro on 2006-09-13
How funny, I finally switched the distro too. I had this constant load, the fan was on all the time and the system crashed after 10-15 mins - this kind of scared me, I really don't want to damage my hardware. I've switched to Gentoo now, my pre-Ubuntu distro, and it's running perfectly. I do hope though that Edgy will run on my hardware when it comes out. I've already filed a bug report about this.

Tom

---

### Post by tschneiter on 2007-02-09
What bios revisions were y'all using?

---

### Post by tsvim on 2007-02-12
Managed fixing the problem by running kernel options notsc nmi_watchdog=0 and blacklisting video module.
Problem seems to be kernel related and present in latest kernels as well according to launchpad bug. According to what I understand it has to do with both processors not being completely synchronized.
Will be editing the wiki after my exam period is finished. One week to go.

---

