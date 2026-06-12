---
title: "Vmware on ubuntu with *nix guest high CPU usage"
date: 2005-11-15
forum: General Help
---

### Post by robert114 on 2005-11-15
Hello 

I'm having a weird "problem" with VMware workstation 5.0.0 build 13124

I'm running a small webserver Ubuntu 5.04 Ubuntu base installation (no X server)on VMWare on a Win 2003 host (P3 1Ghz) without any problem the CPU usage is what i consider low around 1-5%.

But when i transport the Ubuntu 5.04 server to my Ubuntu Breezy install with the same VMWare version on a AMD 2200 proc the CPU usage of the vmware-vmx process goes up to 10%+ when the ubuntu 5.04 server is idle.

This behaviour is a bid odd because i installed my server on this AMD machine and transported it to the P3 Win2003 comp, during this installation proces I didn't look at the CPU-usage, so i haven't any info about it.
Behaviour like this may be expected when the VMware server is build on the older P3 Win 2003 machine. but it isn't.

Now i'm having this rather high CPU usage on my Ubuntu 5.10 AMD machine not only with the Ubuntu 5.04 server but also with pc-BSD and i've tried a fresh VMware install with 5.10 on my AMD Ubuntu 5.10 machine with the same high CPU usage.

Offcourse i've tried a Windows XP guest on the ubuntu AMD 2200 host and Windows doesn't have this problem at all, it runs very smoothly on VMware.

After hours of googling and searching the VMWare forums I havn't been able to solve this "problem" 

I've tried to turn off acpi on both the host and client but it didn't lower the CPU usage. But I feld like the guests were a bit more workable so it might have some effect

I hope someone can shine some light on this tiny problem and i proberly have got to excuse myself for my English since it is not my native language.

Robert.

---

