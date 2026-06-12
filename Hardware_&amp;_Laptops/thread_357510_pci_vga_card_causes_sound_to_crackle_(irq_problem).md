---
title: "pci vga card causes sound to crackle (irq problem)"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by McButt on 2007-02-09
As the title suggest I have problems with my nvidia fx5200 pci videocard. When its put to work by viewing a video file for example, it causes the sound to 'crackle'. I'm using it under ubuntu dapper, using an ecs k75sa mobo with onboard audio. 
I know for sure that the onboard audio is not the cause of the problem, as it's worked flawless for years (and still does with any other videocard I stick in there). Also it's not a problem inherent in the videocard, as using it in an other PC doesn't cause problems (tested on debian etch and ubuntu edgy).

I suspect its an IRQ problem judging bij lspci and dmesg output.
```
piet@jemoeder:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:09.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```

```
piet@jemoeder:~$ dmesg | grep IRQ
[17179571.748000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.748000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.748000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)[17179571.748000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 *12 14 15)[17179571.748000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.748000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179571.748000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)[17179571.748000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)[17179571.752000] PCI: Using ACPI for IRQ routing
[17179572.128000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179576.160000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[17179576.160000] PCI: setting IRQ 12 as level-triggered
[17179576.160000] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[17179576.280000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[17179576.280000] PCI: setting IRQ 5 as level-triggered
[17179576.280000] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[17179588.176000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 5
[17179588.176000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKG] -> GSI 5 (level, low) -> IRQ 5
[17179588.184000] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 5, 00:07:95:b4:3b:12.
[17179588.336000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179588.336000] PCI: setting IRQ 11 as level-triggered
[17179588.336000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179588.752000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179588.752000] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
```
This shows that the vga card and the onboard audio are sharing the same IRQ. 
When I go in the bios and enable the 'Assign IRQ to VGA' option, the vga card gets assigned to IRQ5 making it conflict with something other then the onboard audio, but this doesn't solve the problem.

The only way I got the audio to work properly was to disable the 'Assign IRQ to VGA' option in the bios, and turn of 'ACPI enabled OS'in the bios aswell. This results in the vga card not getting an IRQ at all, see dmesg output below.
```
piet@jemoeder:~$ dmesg | grep IRQ
[   21.551339] PCI: Using IRQ router SIS [1039/0018] at 0000:00:02.0
[   21.551353] PCI: IRQ 0 for device 0000:00:02.1 doesn't match PIRQ mask - try pci=usepirqmask
[   21.551365] PCI: IRQ 0 for device 0000:00:09.0 doesn't match PIRQ mask - try pci=usepirqmask
[   21.929122] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing  enabled
[   25.938190] PCI: Found IRQ 12 for device 0000:00:02.2
[   26.618266] PCI: Found IRQ 5 for device 0000:00:02.3
[   40.372004] PCI: IRQ 0 for device 0000:00:09.0 doesn't match PIRQ mask - try pci=usepirqmask
[   40.372013] PCI: No IRQ known for interrupt pin A of device 0000:00:09.0. Ple ase try using pci=biosirq.
[   40.372018] NVRM: Can't find an IRQ for your NVIDIA card!
[   40.372026] NVRM: [Assign IRQ to VGA] should be set to YES
[   40.512595] PCI: IRQ 0 for device 0000:00:09.0 doesn't match PIRQ mask - try pci=usepirqmask

...those last 4 lines about not having an IRQ for nvidia are then spammed another 20 times, I left them ou there for readability

```

 This cures the sound problem, but gimps videoperformance significantly, the proprietary nvidia drivers wont work at all under these conditions and the opensource 'nv' display very jerky video playback. Not a very nice fix.

I've spent a fair bit of time scourching the internet for solutions or possibilities to assign IRQ's, but I just can't figure it out :(.  
Realy hope someone out there can point me in the right direction, any help would be greatly appreciated :)


edit:
Very, very late edit, but I just found this old post by myself and figured I'd mention how I (eventually) fixed this problem in case someone else might be struggling with a similar problem. It turned out my motherboard (an ecs k7s5a) had a BIOS installed with very poor PCI support. After flashing the newest BIOS onto it all was good. The thing is now running quite well as a media server pc.

---

