---
title: "My new AMD Athlon II X4 640 inexplicably overheats"
date: 2011-01-21
forum: Hardware
---

### Post by fnedrik on 2011-01-21
I have a Athlon II X4 640 CPU with a ASUS M4A785TD-M EVO motherboard and a good quality 450W PSU. I use the included boxed CPU fan, a 120 mm case fan and I do not overclock. I have built many computers the last 15 years and I know how to attach a heat sink, etc.

For some reason my computer shuts down when I max more than one (of four) cores. The output from "sensors" when I am idling is:

[INDENT]$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +76.0°C  (high = +70.0°C, crit = +99.5°C)  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.39 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.34 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +4.97 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +11.85 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    3479 RPM  (min =  600 RPM)
CHASSIS FAN Speed:1369 RPM  (min =  600 RPM)
POWER FAN Speed:     0 RPM  (min =  600 RPM)
CPU Temperature:   +36.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +42.0°C  (high = +45.0°C, crit = +75.0°C)[/INDENT]

These values are measured after I have turned of AMD Cool'n Quiet and the BIOS "smart fan" option. The measurements with those turned on (as per default) are slightly higher but essentially the same.

Note the extreme difference in opinion on what my CPU temperature is. k10temp says that my CPU is idling on 76 degrees C! The normal ACPI interface says that the CPU is a slightly high, but decent enough 36 degrees C. When I add one 100% job (for example cpuburn, but any cpu intensive task does the trick) k10 reports about 81 deg C and ACPI maybe 42. When I add another one and wait for a couple of minutes, the temp goes up to around 90, according to k10 and then the computer shuts down. ACPI still thinks everything is OK and reports maybe 48 on CPU and MB temp and the fan speed has risen from 2800 to 3500. The fan is already idling on 3500 in my printout, since that is measured when I tried to turn of all throttling features in the BIOS, as mentioned above.

When I start up and check my BIOS, it reports the same values as ACPI, i.e that the CPU is fine and not overheating.

What is going on here? Is k10 reporting bad figures? It would seems so - the computer is adequately cooled, does not feel hot to the touch or by the exhaust air and BIOS agrees with the ACPI module. But why then does my computer shut off when I max just two of my four cores?

If it helps, here is my uname and lspci:
[INDENT]$ uname -a
Linux Surver 2.6.35-24-generic-pae #42-Ubuntu SMP Thu Dec 2 03:21:31 UTC 2010 i686 GNU/Linux
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)[/INDENT]

If any of you brainy, knowledgeable and friendly gurus can help me, I will be eternally grateful.

---

### Post by paulisdead on 2011-01-21
Since the BIOS agrees with ACPI, I'd say that's probably the correct temp.  76C would be noticeably hot, so if you want to double check, you could carefully touch the heatsink and see how hot it is.  I'd expect you can ignore the temp from k10.

---

### Post by fnedrik on 2011-01-21
But _why_ does the computer shutdown automatically every time I run 2 100% processes? Is it because the thermometer on the CPU (which is what k10temp checks, I think) is faulty, so the CPU demands shutdown all by itself?

Or is it something unrelated to temp? Power failure? Seems unlikely. I have no optical drive, just one hard drive and I am using the on-board graphics, so the rig should not draw much current.

Or is the Linux kernel monitoring this and freaking out and doing an emergency shutdown all by itself (I see nothing in the logs, but then again, maybe it has to make a panic shutdown quickly). This would also seem unlikely. The kernel would have to be extremely sure that it has the correct drivers to do such a thing.

Or is my CPU really overheating? Even if my cooling is inadequate in some way, should not the CPUs nowadays just scale down the frequency and continue?

---

### Post by paulisdead on 2011-01-21
That's why it might not be a terrible idea to get an idea what the actual temp is.  Try touching the heatsink carefully, and just see if it's really that hot.  76C is pretty hot, 36C should just be warm.  You could even hit it with a load until it locks up, and do it right when it shuts down.  It's always a good idea to discharge excess static from your body before touching this stuff, so touch the side of the case or something else grounded before you go poking around inside.

If there's a more up to date version of your bios, you might look into that.  Also, it couldn't hurt to reseat the heatsink on the CPU.

If you're really sure that it's not getting that hot, you can probably find options in the bios for temperature thresholds for throttling and shutdown.  Definitely try a bios update first, though, since they might've fixed the issue.

---

### Post by Yellow Pasque on 2011-01-22
IIRC, there's a way to correct temp readings that are known to be inaccurate (yours seems to be 40C too high). I'm not sure if that would alter the way the CPU reads the temp, or just fix how it displays in sensor output.
If you're confident your CPU is not overheating, you could try blacklisting the k10temp module and see if that stops the shutdown.

> Try touching the heatsink carefully, and just see if it's really that hot. 76C is pretty hot, 36C should just be warm.
76C might be very uncomfortable (even painful) to some people depending on the sensitivity of their finger (you've been warned).

EDIT: You could also try running a later kernel to see if it's a bug in k10temp that's been fixed.

---

