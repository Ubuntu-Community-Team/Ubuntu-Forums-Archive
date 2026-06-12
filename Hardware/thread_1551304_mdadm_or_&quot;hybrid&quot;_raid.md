---
title: "mdadm or &quot;hybrid&quot; raid"
date: 2010-08-12
forum: Hardware
---

### Post by iverasp on 2010-08-12
Hello,

I'm just about to upgrade my server with new harddrives, memory and OS. It used to run Gentoo but I'm switching to Ubuntu 10.04 Server as work and study occupies my time to a degree that I no longer wish to use hours on system upgrades and general maintenance.  The motherboard has a nForce chipset with a RAID controller. I believe this is supported in the recent release of Ubuntu. However, it is of course not fully a hardware RAID solution. I've read about the topic, but, as I've never done RAID before I still feel I should ask someone with experience.

Is there really a difference between this "hybrid" RAID of the nForce chipset and the software RAID of mdadm in the kernel? The configuration is two 1TB drives in RAID1 (mirroring) with an AMD64 3000+ (1,8GHz) and 1Gb DDR1 memory on a gigabit network. Would the nForce RAID take any load of the CPU or does it, as I see it, only provide a commercial clever solution for those running Windows? I'm also tempted to buy a Sil3134 RAID controller for support for SATA2 as my motherboard only supports SATA1, but, as increased speed is not an issue, just a luxury, it seems a waste as I don't see how that tiny chip on the controller really provides any offload for the CPU.

All input welcome, thank you.

---

### Post by Fafler on 2010-08-12
There shouldn't be any performance difference. I'd go for the mdadm solution any day. With the onboard RAID, you can't move the RAID to a new board, except if it uses the same chipset. With mdadm you are free to upgrade to any board or PCIe card you want.

SATA 1 vs SATA2 shouldn't give much real world performance difference.

---

### Post by realzippy on 2010-08-12
Read this?

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Advantage fakeraid:
Multiboot with Windows possible on same array
Broken HD can be changed without booting the OS

Never tried my onboard fakeraid but running 
software RAID0 for years.No problems and pretty fast..

---

### Post by iverasp on 2010-08-12
Just as I thought then. Tank you for the input. When benchmarking my SATA drives in my workstation I see a 33% increased performance (75MB/s vs 100MB/s, hdparm -tT) for SATA1 vs SATA2. Would this make a difference when accessing files over gigabit ethernet (under 10 users) or would it feel pretty much the same?

EDIT: Thanks for the link realzippy

---

### Post by Fafler on 2010-08-12
SATA *should* be able to deliver approx. 145 mb/s and SATA II 290 mb/s. Might just be a better chipset?

Gigabit ethernet is able to transfer just below 100 mb/s, so if your SATA controller cant deliver that, it might actually be worth upgrading.

---

### Post by Fludizz on 2010-08-12
I'd go for mdadm raid rather then fakeraid :) 
Easier to recover if the hardware controller fails: Just plug the disks into a new controller and mdadm will pick up the array and continue happily as if nothing has happened.

The differences between SATA1 and SATA2 are not really noticable unless when you use high end disks (SSD's for example). But then again, if you'd go high end, you'd be using hardware RAID cards ;)

---

### Post by iverasp on 2010-08-12
The drives are on the same controller (onboard). I'll benchmark the throughput of data from the drives in my workstation over gigabit ethernet later. If I still see a 33% increased performance I might invest in a new controller.

Thanks for all input, the decision is now final and the drives are arriving today.

---

