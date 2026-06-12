---
title: "amd74xx in hardy?"
date: 2008-06-07
forum: Hardware
---

### Post by Futures on 2008-06-07
Hello fellas, first im quite new to ubuntu, but with your help i will try my very best :guitar:

The Problem is, that after a clean install of hardy, the transfer between usb drives and my internal drive is very slow (11 - 19 Mbs). I googled the web and found some hits about setting on DMA and loading the amd74xx module in /etc/modules, but that didnt work out the right way.
I've tried to load the module manually with "modprobe amd74xx" but it gives me an error back: FATAL Module amd74xx not found.

It would be great to get some support setting up right an nforce4 chipset on hardy =)

so the fact about the PC:

- AMD Athlon 3200+
- Gigabyte GA-K8NF-9 (nForce 4 Chipset!) Raid is not in use.
- DVD/CDRW Drive via ATA
- internal IDE Disk via sata (Bios is set to IDE mode)
- 1GB Ram
- and a Zyxel G220 USB Wireless Stick (works fine)

If i have to give you some outpu like lsmod grep or something pls just tell me, because im net to ubuntu i dont know wich information is important for you guys.

And i didnt find anything how i can install the amd74xx module, any ideas?


hope well figure it out ;) sorry for my bad english !

futures

---

### Post by jlcooke on 2008-12-19
> **Futures said:**
> The Problem is, that after a clean install of hardy, the transfer between usb drives and my internal drive is very slow (11 - 19 Mbs).

This is a normal rate.  Nothing to fix.

[QUOTE=Futures;5135345]...
I've tried to load the module manually with "modprobe amd74xx" but it gives me an error back: FATAL Module amd74xx not found.

It would be great to get some support setting up right an nforce4 chipset on hardy =)
...
[/QUOTE}

That would be great.  I second that - specifically the 7th, 8th, 9th, 10th sata drive ports (I assume is also part of the force4/nForce590SLI chipset)

---

### Post by RJARRRPCGP on 2008-12-19
That error may be caused by not using *sudo*!

---

