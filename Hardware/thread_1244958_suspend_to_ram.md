---
title: "suspend to ram"
date: 2009-08-20
forum: Hardware
---

### Post by timalot on 2009-08-20
Hi

Suspend to RAM works on my desktop PC, problem is the video card does
not display anything.

I boot to runlevel 1, run pm-suspend and then resume using the case
button. No luck.

I've tried the quirk options to pm-suspend command plus used the
vbetool directly. No luck. I've also had no luck suspending in X
running the nv driver. (works with binary driver but is unstable for
me)

Any ideas?


Info:
Core 2 Duo 4gb ram
64bit Ubuntu Jaunty.
lspci output:

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
        Subsystem: XFX Pine Group Inc. Device 2372
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=512M]
        Memory at e0000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Expansion ROM at <ignored> [disabled]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information <?>
        Kernel modules: nvidiafb

---

### Post by condamine on 2009-08-28
Have you installed the Proprietary hardware driver for your video card?

Once I changed from the default nvidiafb kernel module to the latest one available under System -> Administration -> Hardware drivers.... suspend worked fine

Here´s the output for my video (Dell XPS M1330) using ¨lspci -vv¨

> 01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
	Subsystem: Dell Device 0209
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f2000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at ef00 [size=128]
	[virtual] Expansion ROM at f4000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

---

### Post by timalot on 2009-09-03
Yes the binary driver works for me. 

I would like to use the open source driver, as the binary drivers are usually not as good / support is not as good. (Under load it *seems* to stuff up the task/io scheduling for me)

But I have given in and am using the nvidia binary driver that is installed by ubuntu and suspend/resume works ok.

Thanks
Tim

---

