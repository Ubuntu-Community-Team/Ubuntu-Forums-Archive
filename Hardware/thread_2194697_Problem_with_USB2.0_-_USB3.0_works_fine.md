---
title: "Problem with USB2.0 - USB3.0 works fine?"
date: 2013-12-20
forum: Hardware
---

### Post by luge86 on 2013-12-20
Hi folks,

i've got a new PC with the following hardware setup:
> Gigabyte GA970-U3
AMD FX6300
ADATA 2*4Gb RAM @ 1600 MHz
Kingston 120 Gb SSD

I'm running Kubuntu 13.10 and my system is up-to-date.

The mainboard contains all kind of USB ports (1.1, 2.0, 3.0).
lspci lists all controllers:
> lugge@lugge-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx1 port A)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8500 GT] (rev a1)
02:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
04:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
05:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)


If i connect all my USB devices to a 3.0 port, i get the following lsusb:
> lugge@lugge-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 004: ID 18a5:0302 Verbatim, Ltd 32GB Flash Drive
Bus 006 Device 003: ID 0bb4:0ffe HTC (High Tech Computer Corp.) Desire HD (modem mode)
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 003: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 004 Device 002: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Now, when i remove the USB flash drive and my Smartphone from USB3.0 and plug them into USB2.0 they are not being listet:

> lugge@lugge-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 003: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 004 Device 002: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I wonder why the kernel does not recognize my devices via USB2.0 Windows 7 just works fine.

Interessting thing: in GRUB2, my keyboard works fine on every USB2.0, but after the kernel was loaded, it does not.

If you need more information, please let me know.

Greetings,
lugge

---

### Post by varunendra on 2013-12-21
Please see this post that tries to describe how internal hubs (in the chip) are shared with external ports : [http://ubuntuforums.org/showthread.php?p=12879260](http://ubuntuforums.org/showthread.php?p=12879260)

Combined with your description, we can clearly see in above outputs you posted that even though you connected the devices to USB3 ports, they were internally connected to USB2 hubs. I believe it is this internal switching mechanism that gets stuck itself (more likely), or confuses the kernel somehow.

In the former case, it helps to just power off the system for a few minutes *(anything from 2 to 30 minutes, usually depending on how powerful those filter capacitors are that need to be completely drained to reset the chip)* then power it on again. In the latter case (kernel confusion), it may help to boot with no or only basic devices (like keyboard, mouse) connected, then connecting the rest of the devices after the OS is fully loaded.

To see the device-hub connection in a tree view, you can use -
```
lsusb -t
```

Please post the outputs of the above command from a few working/non-working combinations, with a description of what you connected to which port, and when (preboot, or after the OS was loaded). Taking a look at syslog and dmesg can also give some clues on what (and if something) is happening in the background when you plug or switch the connected devices.

I'm no expert on this and can't say if your problem is something similar or something entirely different, just sharing what I have personally observed and learned (from the datasheets of a few USB chips). Hope this info and accordingly your observations and feedback can at least help expanding our knowledge on it, and possibly direct us to a solution too.

---

