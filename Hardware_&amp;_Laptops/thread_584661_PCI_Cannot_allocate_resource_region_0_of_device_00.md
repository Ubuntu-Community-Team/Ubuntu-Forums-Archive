---
title: "PCI: Cannot allocate resource region 0 of device 0000:00:00.0"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by kyselejsyrecek on 2007-10-21
Hi,

I installed Ubuntu 7.10 (gutsy) desktop edition a few days ago.
When I ran it first, I got the following error (or warning/alert/notice - I don't know) when booting:

```
PCI: Cannot allocate resource region 0 of device 0000:00:00.0
```

I got this error also in Ubuntu 7.10 server, but I never seen it in lower versions of Ubuntu and I'm really not sure, what does it mean.
It's also important, that it doesn't stop booting, it only shows this warning/error.. and continues normal.

I also tried "dmesg | grep PCI" with this result(s):

```

[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[   21.541096] PCI: Using configuration type 1
[   21.548714] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.548720] PCI: Probing PCI hardware (bus 00)
[   21.549946] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.569506] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   21.569594] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   21.569677] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   21.569758] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   21.569840] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   21.569922] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   21.570004] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   21.570086] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   21.572581] PCI: Using ACPI for IRQ routing
[   21.572583] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[COLOR="Red"][   21.572615] PCI: Cannot allocate resource region 0 of device 0000:00:00.0[/COLOR]
[   21.583705] PCI: Bridge: 0000:00:01.0
[   21.583729] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.266409] PCI: VIA PCI bridge detected. Disabling DAC.
[   30.257465] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   32.195510] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
[   32.909132] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   32.909150] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   35.546858] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[   35.654336] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
[   35.758196] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
[   35.862049] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
[   35.966073] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 23
[   35.966896] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   43.101433] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.273584] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.570283] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[   43.570305] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[   44.149757] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 17 (level, low) -> IRQ 17
[   44.149768] ACPI: PCI interrupt for device 0000:00:09.1 disabled
[   44.428042] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   44.428182] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   56.061897] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16

```

Also the previous line is interesting, but I don't know, where I should use this.

My configuration:

Ubuntu 7.10 (desktop & server) - 2.6.22-14-generic/2.6.22-14-server
AMD Athlon 64 2800+ (overclocked from 1.8GHz to 2GHz)
RAM GEIL - 2*1GB - DDR 333MHz
2HDDs: SEAGATE 80GB - IDE interface
             SEAGETE 320GB - SCSI interface
ATI Radeon 9550 graphic card

Thanks for reply,
                                                                                                                  Luká&#353; Chmela

---

### Post by mikewhatever on 2007-10-21
That error message is a somewhat known one, but usually harmless. I saw it in different variations in Edgy Feisty and now Gutsy, and if you google it, it is all over the web. You should test your new install for some time to make sure things work or otherwise and file a bug report at launchpad.net. Several ones have been filed already though [https://bugs.launchpad.net/bugs/+bugs?field.searchtext=Cannot+allocate+resource+region&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=Cannot+allocate+resource+region&search=Search+Bug+Reports&field.scope=all&field.scope.target=)

---

### Post by bdoe on 2007-10-28
I am also having this issue (have not captured my dmesg output, but the thing flashing on the screen is identical).  However, my system does *not* boot exactly normally.  After this message flashes across the top of the screen, the screen goes dark, the hard drive flickers once every few seconds, there's no boot screen, and it takes nearly three minutes for boot to complete.  Everything is fine after that.
 
When I boot in safe mode, everything seems fine, and it boots to console inside of 30 seconds.  Typing "gdm" at the console prompt brings up the familiar Gnome interface very quickly.
 
I never had this problem with Feisty, nor did I have it when booting off the Gutsy Live CD.
 
Can anyone help me figure this out?  It's getting really annoying.

---

### Post by wateenellende on 2007-11-04
According to
[http://www.linuxforums.org/forum/suse-linux-help/76822-3-pci-cannot-allocate-resource-region-0-device.html](http://www.linuxforums.org/forum/suse-linux-help/76822-3-pci-cannot-allocate-resource-region-0-device.html)
it might be related to ATI graphics cards.

I have the same message, and an ATI card.

---

### Post by granny6989 on 2007-11-07
Not ATI only, I have it on a GeForce card. Never saw it until I moved up to Gutsy when it came out..... Any help or remedy would be appreciated. also seems to be more of a problem with the 64 bit setup. msi motherboard, evga PCIe card with Nvidia chips is what i'm runnin'.

S*


X*X*X*X*X*X*X  adding this edit instead of a new post  X*X**X*X*X*X*X*

    I went through a bunch of uploading/reloading last weekend. It seems that I only have this problem with Gutsy release in 64bit. If I reload Gutsy as 32 and install everything, I get no errors, full compiz, and so far a very stable platform. Not sure what the exact deal is, but I am fine running everything like this, even though I may be giving up a bit of performance by not using 64 bit OS. I ran Feisty as 64bit for about three weeks before the new release, and didn't have the error message with my PCI. I *was *having problems getting compiz to run, even in that scenario. Again, not sure why, I am just experimenting to get the best running system I can.....

currently:
MSI K8M890M2-V board
Athlon 3500+
EVGA e-GeForce 7100GS

---

### Post by bdoe on 2007-11-08
It seems to be a Northbridge problem.  According to lspci (and backed up by Windows Vista's hardware manager), the device in question is my northbridge, or - more specifically - my CPU to PCI bridge:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 755 Host (rev 01)
```

---

### Post by Monosabio on 2007-11-10
I have just flashed my mainboard Bios to a newer version and now I get the same error.
Everything appears to work fine but it is annoying to see that error while starting Ubuntu.

```

[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:becf0000)
[   71.326737] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[   71.326740] PCI: Using configuration type 1
[   71.326741] Setting up standard PCI resources
[   71.347287] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   71.347306] PCI: Probing PCI hardware (bus 00)
[   71.347777] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   71.347781] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   71.348336] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   71.348403] PCI: Transparent bridge - 0000:00:1e.0
[   71.348431] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   71.348533] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   71.348605] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   71.350834] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   71.350987] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   71.351137] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   71.351293] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   71.351471] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[   71.351622] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   71.351771] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   71.351922] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   71.354727] PCI: Using ACPI for IRQ routing
[   71.354731] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[COLOR="Red"][   71.354742] PCI: Cannot allocate resource region 0 of device 0000:00:00.0[/COLOR]
[   71.390090] PCI: Bridge: 0000:00:01.0
[   71.390108] PCI: Bridge: 0000:00:1e.0
[   71.390137] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   82.592473] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   82.592488] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   82.696145] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   82.696160] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   82.799938] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   82.799950] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   82.903764] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   82.903780] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   83.008668] ACPI: PCI Interrupt 0000:02:02.2[B] -> GSI 18 (level, low) -> IRQ 18
[   83.080342] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[ff906000-ff9067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   83.080442] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 17 (level, low) -> IRQ 19
[   83.132235] ohci1394: fw-host1: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[ff904000-ff9047ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   83.142297] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   83.169894] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   83.169902] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   83.169945] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   84.467049] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   84.467092] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   84.904033] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 21
[   84.904054] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   84.905627] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   91.912809] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   92.038958] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   93.706242] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 19
[  101.946746] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16

```

I'm using for Ubuntu 7.10 a Mainboard Intel 865PERL + ATI 9700 Pro AIW

---

### Post by 4nDr3s on 2007-11-10
Hi!! 
i have the same error as you. 
I'm running a SiS Chipset, on a amd athlon 64 3700+. 
When i was running dapper drake amd64 i didnt have that error.
The last version i was running was edgy eft i386 and i didnt have that message aswell...

Additionally to that, i dont get the boot splash while loading ubuntu... i just get a back screen and after a while i get the login window.

---

### Post by cogitordi on 2007-11-11
> **4nDr3s said:**
> 
I'm running a SiS Chipset, on a amd athlon 64 3700+. 
When i was running dapper drake amd64 i didnt have that error.
The last version i was running was edgy eft i386 and i didnt have that message aswell...


ATI 9600 Pro AGP with NForce chipset, AMD64 3400+. Gutsy/64. Same message here. Never saw this in previous versions of Ubuntu.

By the way, do you have the Socket 754 3700+ or the Socket 939?

---

### Post by 4nDr3s on 2007-11-11
> **cogitordi said:**
> ATI 9600 Pro AGP with NForce chipset, AMD64 3400+. Gutsy/64. Same message here. Never saw this in previous versions of Ubuntu.

By the way, do you have the Socket 754 3700+ or the Socket 939?

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 755 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:09.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
00:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```

---

