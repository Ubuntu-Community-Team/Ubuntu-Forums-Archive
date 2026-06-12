---
title: "ACPI hang at startup, debug info included"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by debackerl on 2008-03-02
Hello,

I have trouble to active ACPI on my latop. I have tested the following switches:

```
acpi=ht		OK
pci=noacpi	HANGS
acpi=noirq	HANGS
pnpacpi=off	HANGS
noapic		HANGS
nolapic		HANGS
```

When it is marked 'HANGS' it means that the kernel hangs at startup.

Consequently, I have compiled a custom kernel with the ACPI debug value set to yes. Here are the last few lines with acpi_dbg_layer=0xffffff and acpi_dbg_level=0xffffff:

```
ACPI: Core revision 20070126
ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Parsing all Control Methods:
Table [DSDT](id 0001) - 551 Objects with 52 Devices 153 Methods 13 Regions
 tbxface-0587 [02] tb_load_namespace     : ACPI Tables successfully acquired
ACPI: setting ELCR to 0800 (from 0020)
evxfevnt-0091 [02] enable                : Transition to ACPI mode successful
CPU0: Intel(R) Pentium(R) 4 CPU 2.60Ghz stepping 07
```

I tried to use APM instead, but dmesq repports: "apm: BIOS not found", and there is not APM option in the PhoenixBIOS. The laptop is a Cybercom (made by MEDION). I am using Ubuntu Gutsy.

Any help would be greatly appreciated :(

Laurent.

---

### Post by gn2 on 2008-03-02
My son's Medion laptop is a Pentium 4 2.66ghz, I forget the model number, what worked was acpi=off

---

### Post by debackerl on 2008-03-02
Yes I know, and acpi=ht works too as written above. The question is, what fails in the kernel, how can I debug the ACPI module, or is there a submodule to desactive? The fact is that I want to read the battery level, control CPU frequency, and prevent the fan from running full speed. There is no way I can use linux in the current state. I appologize if I was not clear :)

PS: I am a software developer, but not a kernel hacker.

---

### Post by gn2 on 2008-03-02
On my son's laptop the fan operates correctly using acpi=off, it only speeds up when required.
acpi=off has worked with PCLinuxOS and Mint Daryna on that laptop.
Don't know about battery monitoring as he uses it on mains all the time.
Sorry I can't be more help.

PS: I'm neither a software developer or a kernel hacker, I just get it working then leave it alone! :D

---

### Post by debackerl on 2008-03-02
Yes, thanks for your help, I just said that I'm a soft developer, to say that people could ask me to perform a bit of debugging. With my laptop, I did notice that the fan makes less noise with Windows XP than Ubuntu Gutsy with acpi=ht.

In addition, it appears that the laptop worked fine with Breezy an Dapper: [https://wiki.ubuntu.com/LaptopTestingTeam/MedionMD6200](https://wiki.ubuntu.com/LaptopTestingTeam/MedionMD6200) , so it is likely a regression in the linux kernel between version 2.6.15 and 2.6.22 (apparently, 2.6.12 was also ok). So this is more serious than I thought. Is there some kernel guru in this forum who know what went on during that time span? I would really love to keep 2.6.22, because I do not think that 2.6.15 supported NTFS so well.

---

### Post by debackerl on 2008-03-02
I have installed the 2.6.24-11 generic kernel from Ubuntu Hardy, and it seems to works well. Except that x.org is broken then. So I suppose that I need to find a distro with native 2.6.24.

---

