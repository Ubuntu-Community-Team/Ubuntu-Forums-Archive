---
title: "Problems with dual EVGA Geforce GTX220"
date: 2009-11-23
forum: Hardware
---

### Post by torenvln on 2009-11-23
I have a i7core chip on an EVGA X58 SLI LE MOBO with an EVGA GE FORCE GTX 220 video card running Ubuntu 9.10 64. This configuration with the [[COLOR=blue][COLOR=blue! important][FONT=Verdana][COLOR=blue! important][FONT=Verdana]NVidia [/FONT][/COLOR][COLOR=blue! important][FONT=Verdana]drivers[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") works fine all the way up to the dual DVI for dual heads - I've been really pleased with it. 

I decided to add a second EVGA GEFORCE 220 so I could go four wide with my monitors.

When I [[COLOR=blue][COLOR=blue! important][FONT=Verdana][COLOR=blue! important][FONT=Verdana]plug [/FONT][/COLOR][COLOR=blue! important][FONT=Verdana]in[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") the second card the system won't load the kernel.

From the GRUB menu, loading of the generic kernel halts at 
"PANIC: early exception 0e rip 10:ffffffff812d00ec error 9 cr2 ffffffffff400444"

Loading of the generic kernel in recovery mode halts at the same as above.

lspci (with one video card plugged in) gives:
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:09.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub [[COLOR=blue][COLOR=blue! important][FONT=Verdana][COLOR=blue! important][FONT=Verdana]System [/FONT][/COLOR][COLOR=blue! important][FONT=Verdana]Management[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) [[COLOR=blue][COLOR=blue! important][FONT=Verdana][COLOR=blue! important][FONT=Verdana]USB[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GT 220] (rev a2)
02:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
06:00.0 Ethernet controller: Realtek [[COLOR=blue][COLOR=blue! important][FONT=Verdana][COLOR=blue! important][FONT=Verdana]Semiconductor[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

I'm guessing I need to either change my [[COLOR=blue][COLOR=blue! important][FONT=Verdana][COLOR=blue! important][FONT=Verdana]BIOS[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") settings or more probably find some wisely chosen boot parameters... I'm no expert though... can anyone tell I need to do to get the system booting with two video cards plugged in?

---

### Post by torenvln on 2009-11-24
But wait there's more... 

When I boot up the recovery mode image(ubuntu 9.10 64)  from grub I get to the following line in the boot and it hangs

[    1.488092] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086:3a16]

This all worked (and still does) with only one card.   IRQ problem obviously... but what to do about it?

---

