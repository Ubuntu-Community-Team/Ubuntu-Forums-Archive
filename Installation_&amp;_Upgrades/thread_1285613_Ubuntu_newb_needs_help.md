---
title: "Ubuntu newb needs help"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by SmartyJones on 2009-10-07
After friends have finally talked me into trying Ubuntu I order the disk and it arrived today I bought a new Hard Drive (500GB) and installed windows XP on 270GB of it leaving 200GB open for an Ubuntu install. I put my new Ubuntu 9.04 Desktop Edition cd in and restart my pc  and get this error:

> [  96.906455] [Firmwarebug]: powernow-k8: your BIOS does not provide ACPI_PSS objects in a way that linux understands. Please report this to the Linux ACPI maintainers and complain to you BIOS vendor.

[  96.906563] [Firmwarebug]: powernow-k8: your BIOS does not provide ACPI_PSS objects in a way that linux understands. Please report this to the Linux ACPI maintainers and complain to you BIOS vendor.

Loading please wait ...

BusBox v131032(ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash) Enter 'help' for a list of built'in commands

(initramfs) _My intentions are to have both OS's on same Hard Drive, My question is do I need to uninstall widows and put Ubuntu on first and Windows 2nd? or should this work? Not really sure what is going on and/or why I can't get it to install, any helpful advise or constructive criticism is greatly appreciated!

System Specs:
WindowsXP professional SP3
AMD Athlon 64x2 Dual Processor 5000+
2.60 GHz
3.00GB RAM
Western Digital 500GB HD
(with 200GB partitioned off for this install)

---

### Post by dreza on 2009-10-08
Bios issues have nothing to do with windows, it means your base system below windows or linux isnt agreeing with linux. Post the brand and model of your comp, or if custom the motherboard. Someone may be able to help but they are gona ask for that info.

---

### Post by SmartyJones on 2009-10-11
So when I run the dxdiag command and check the system tab it says this about the bios:

> BIOS: BIOS Date: 05/04/08 16:19:08 Ver: 08.00.15The brand of motherboard is XFX

but after a more in depth search here is the info I've come up with:
> 
**[SIZE=2]Processor a[/SIZE]**             **[SIZE=2]b[/SIZE]**      [SIZE=2]2.60 gigahertz AMD Athlon 64 X2 Dual Core
256 kilobyte primary memory cache
1024 kilobyte secondary memory cache
64-bit ready
Multi-core (2 total)
Not hyper-threaded[/SIZE]> 
**[SIZE=2]Main Circuit Board[/SIZE]**
[SIZE=2]Board: XFX MI-A78S-8209 Ver1.1
Bus Clock: 200 megahertz
BIOS: American Megatrends Inc. 080015  05/04/2008[/SIZE]

hope this helps you (all) to be able to help me so I can finally run Ubuntu

Thanks in advanced.

---

### Post by p2bc on 2009-10-11
It is definitely a bios issue. 

You should see if there is a firmware update for your BIOS. Might also replacing you BIOS altogether with [Coreboot](http://www.coreboot.org/Welcome_to_coreboot) A lot of board are being shipped with it pre-installed, and it will allow you to have a lot of freedom. It is an option. Just saying  :-)

---

