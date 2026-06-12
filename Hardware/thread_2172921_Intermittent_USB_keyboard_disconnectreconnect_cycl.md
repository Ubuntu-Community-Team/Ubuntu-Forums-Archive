---
title: "Intermittent USB keyboard disconnect/reconnect cycles"
date: 2013-09-07
forum: Hardware
---

### Post by Calin_Morar on 2013-09-07
I have an USB Unicomp keyboard (rather nice even if not as nice as the original IBM Model M) but something is fishy. 

Running Ubuntu 13.04 64bit with latest kernel  -   on a Core I7 with MSI X58 Platinum SLI mobo with nvidia gforce vid

Kernel version:

Linux obelix 3.8.0-22-generic #33-Ubuntu SMP Thu May 16 15:17:14 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


If I run with ACPI on the system is literally driving me nuts; it cycles disconnect/connect the keyboard almost every minute and is truly annoying to loose chars while you type. With ACPI off in BIOS or with  acpi=off or noapic nolapic  kernel options all is nice and dandy - no disconnects. I've tried pci=XXX options .. bugger .. none of them work. Pretty much I tried to make the kernel not use ACPI for interrupts rerouting so I don't loose SMP - as soon as there is a trace of APIC use disaster strikes. 

Obliviously with ACPI/APIC off i loose SMP and HT ... I can literally see serious performance degradation since I am running only in a single core. 

Usually the system is stable with default options even if KB goes nuts.

NO is not HW; all my other USB devices never get cycled on this machine; tested the KB on a toshiba laptop running linux 12.04 no disconnects (sorry no Windows machine - i use exclusively Linux by many years) . I suspect some freak odd combination between my motherboard IOAPIC, Unicomp KB and kernel APIC drivers. I suspect also that this APIC thing is messing with my sound because plymouth is also being restarted from time to time with ACPI on.

Anyone any idea ?

---

### Post by Calin_Morar on 2013-09-07
Managed to find a fix; I had to downgrade the BIOS version to the very first revision available 3.00 and finally the USB disconnects are gone. 

So for those that have an MSI X58 Platinum SLI misbehaving get the bios v3.000 from here [http://download7.msi.com/download_files/mb/bos_exe/7522v30.zip](http://download7.msi.com/download_files/mb/bos_exe/7522v30.zip) , downgrade and things shoud get to normal.

IOAPIC enabled all no matters, USB diconnects are gone; still have to confirm the sound issues are gone but everything so far is looging OK.

---

