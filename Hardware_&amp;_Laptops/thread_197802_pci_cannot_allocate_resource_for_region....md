---
title: "pci cannot allocate resource for region..."
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by flan on 2006-06-16
Hello,
I have an acer aspire 1652 wlmi laptop. I've installed Dapper and it seems almost everything works.

When i boot up the laptop, a sequence of error is displayed :
```

[COLOR="Red"][17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2[/COLOR]

```
but the booting process ends fine, and everything seems ok...

if i do
```
dmesg | grep PCI
```
it shows:
```

[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[17179570.476000] PCI: PCI BIOS revision 2.10 entry at 0xfd7be, last bus=7
[17179570.476000] PCI: Using MMCONFIG
[17179570.788000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.788000] PCI: Probing PCI hardware (bus 00)
[17179570.788000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179570.788000] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[17179570.788000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.788000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.788000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.796000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[17179570.796000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179570.796000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[17179570.796000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.796000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179570.796000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[17179570.796000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179570.796000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179570.796000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179570.796000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179570.796000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[17179570.800000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179570.824000] PCI: Using ACPI for IRQ routing
[17179570.824000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[COLOR="Red"][17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2[/COLOR]
[17179570.836000] PCI: Bridge: 0000:00:01.0
[17179570.836000] PCI: Bridge: 0000:00:1c.0
[17179570.836000] PCI: Bridge: 0000:00:1c.1
[17179570.836000] PCI: Bridge: 0000:00:1c.2
[17179570.836000] PCI: Bus 7, cardbus bridge: 0000:06:01.0
[17179570.836000] PCI: Bridge: 0000:00:1e.0
[17179570.836000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.836000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.836000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179570.836000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.836000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 169
[17179570.836000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.836000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179570.836000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179570.836000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.836000] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179570.836000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.836000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.836000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179570.836000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.836000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 169
[17179570.836000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.836000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179570.836000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179571.236000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 233
[17179571.236000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[17179573.060000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179573.060000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 185
[17179574.872000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 50
[17179574.872000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.980000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 58
[17179574.980000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.084000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179575.084000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.188000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179575.188000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179575.292000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 50
[17179575.292000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.292000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179589.096000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.244000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.996000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 177
[17179589.996000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179591.232000] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179591.232000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179591.232000] Yenta: Routing CardBus interrupts to PCI
[17179591.464000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 185
[17179591.464000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[17179591.464000] pcmcia: parent PCI bridge Memory window: 0xc8200000 - 0xc82fffff
[17179591.464000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x32ffffff
[17179591.468000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179591.472000] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179630.136000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169


```

and here the result of lspci:
```

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
[COLOR="Red"]0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)[/COLOR]
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
0000:06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 02)

```

it could be a pci express problem, but my video card (ati mobility radeon X300) seems to work fine...

i can't figure out where the problem is and how to fix this issue...
someone could help me?

---

### Post by susscorfa on 2006-08-01
i have the same laptop and the same "proble:m does some one know some thing about it?

---

### Post by der_hansen on 2006-08-13
Hello flan,

I got the same Problem but with a X600 Mobility. But X works only with VESA driver. ati, fglrx or radeon don't work.

Also only allocation of Port 2 won't succeed:

dmesg:
```

[17179572.732000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179572.732000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179572.732000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1

```
lspci:
```

0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)

```


Did you get it to work so far?


sicerly,
der_hansen

---

### Post by missingxtension on 2006-09-13
i get the same proglem but with an AIW9800 everything works fine but the sound and its because i changed mother boards and havent been able to fix my Soundcard


```

```0000:00:1f.5 Multimedia audio controller: Intel Corporation
82801EB/ER (I CH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Intel Corporation Desktop Board D865GBF
        Flags: bus master, medium devsel, latency 0, IRQ 201
        Memory at ffa00400 (32-bit, non-prefetchable) [size=512]
        Memory at ffa00800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>
```

```
then dmesg grep pci

```
sh-3.1$ dmesg dmesg | grep PCI
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 30000000:cecf0000)
[17179571.500000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[17179571.500000] PCI: Using configuration type 1
[17179571.504000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.504000] PCI: Probing PCI hardware (bus 00)
[17179571.508000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[17179571.508000] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[17179571.508000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.508000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.508000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.512000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179571.512000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[17179571.516000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179571.516000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[17179571.516000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179571.516000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179571.516000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[17179571.516000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.516000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.516000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179571.520000] PCI: Using ACPI for IRQ routing
[17179571.520000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.520000] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[17179571.528000] PCI: Bridge: 0000:00:01.0
[17179571.528000] PCI: Bridge: 0000:00:1e.0
[17179571.528000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179581.828000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 18 (level, low) -> IRQ 169
[17179582.268000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179582.268000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179582.268000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[17179584.476000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 169
[17179584.476000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179586.264000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179586.264000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179586.372000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[17179586.372000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179586.476000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 169
[17179586.476000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179586.580000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 177
[17179586.580000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179586.684000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[17179586.684000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179586.684000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179596.804000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179596.804000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.328000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
[17179597.328000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179598.632000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 209
[17179615.608000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 177
sh-3.1$

```

well i guess the only help i need is identifyin the device 
ill tkae care of the rest myself

---

### Post by MrSoussey on 2007-01-14
try a bios update... worked for me

---

### Post by flan on 2007-02-05
even updating the bios doesn't work... the warning is still here :confused:

---

### Post by commonplace on 2007-02-07
No fix for this one yet? My wife's Compaq Presario C301NR laptop has the same messages on startup. Everything works fine, so it's merely cosmetic, but when you're trying to get people to switch from Windows to Linux, it doesn't look good -- cosmetics do matter. And it must indicate SOMETHING, even if everything appears fine, though I don't know what.

/Kevin

---

### Post by lamegaptop on 2007-02-07
I am seeing this same annoying error on my HP DV8408us lappy. I would be interested in a fix if anyone comes up with one.

---

### Post by flan on 2007-02-09
> **commonplace said:**
> No fix for this one yet? My wife's Compaq Presario C301NR laptop has the same messages on startup. Everything works fine, so it's merely cosmetic, but when you're trying to get people to switch from Windows to Linux, it doesn't look good -- cosmetics do matter. And it must indicate SOMETHING, even if everything appears fine, though I don't know what.

/Kevin

I think it isn't only a cosmetic issue, It can't read battery state, it is the same on your laptop?

---

### Post by moebious on 2007-12-07
I am having the same issue, however one thing that I noticed that is not working right is that the slash screen that usually shows up with the progress bar. does not show. I am running a Toshiba A45-S120, Ubuntu 7.10. I ran the OS from the liveCD with no issues, and my USB ports seem to be working fine. Cosmetic or not it should work, and would like to fix it. I would at least like to know what is wrong.

---

