---
title: "Debugging kernel panics"
date: 2008-11-10
forum: General Help
---

### Post by Ambush Commander on 2008-11-10
Around the time I upgraded to Intrepid Ibex, I've noticed that I've been getting intermittent kernel panics (indicated by the flashing capslock and scroll lock signs), to the point where running Windows is more stable than running Linux! :-O I'm pretty sure it's a hardware incompatibility somewhere, but when I get a kernel panic, it kernel panics hard, and I don't really get any useful debugging information out of it.

My question to you is this: How do I figure out what is causing the kernel panic?

Some system stats:

Dell Vostro 1400
Ubuntu 7.10 Intrepid Ibex, with Debathena

Lightly edited output of hwinfo --soft
```
cpu:                                                            
                       Intel(R) Core(TM)2 Duo CPU     T5270  @ 1.40GHz, 1400 MHz
                       Intel(R) Core(TM)2 Duo CPU     T5270  @ 1.40GHz, 1400 MHz
keyboard:
  /dev/input/event2    Broadcom Keyboard
  /dev/input/event1    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Microsoft Notebook Optical Mouse
  /dev/input/mice      Broadcom USB Mouse
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      PS/2 Mouse
  /dev/input/mice      AlpsPS/2 ALPS GlidePoint
graphics card:
                       Intel Mobile GM965/GL960 Integrated Graphics Controller
                       Intel 965 GM
sound:
                       Intel 82801H (ICH8 Family) HD Audio Controller
storage:
                       Intel 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
                       Intel 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
network:
  eth0                 Broadcom NetLink BCM5906M Fast Ethernet PCI Express
  eth1                 Broadcom BCM4310 USB Controller
network interface:
  tun0                 Network Interface
  pan0                 Ethernet network interface
  eth1                 Ethernet network interface
  eth0                 Ethernet network interface
  lo                   Loopback network interface
disk:
  /dev/sda             ST9160823ASG
partition:
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda4            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
  /dev/sda7            Partition
cdrom:
  /dev/sr0             PBDS DVD+-RW DS-8W1P
usb controller:
                       Intel 82801H (ICH8 Family) USB2 EHCI Controller #1
                       Intel 82801H (ICH8 Family) USB UHCI Controller #3
                       Intel 82801H (ICH8 Family) USB UHCI Controller #2
                       Intel 82801H (ICH8 Family) USB UHCI Controller #1
                       Intel 82801H (ICH8 Family) USB2 EHCI Controller #2
                       Intel 82801H (ICH8 Family) USB UHCI Controller #5
                       Intel 82801H (ICH8 Family) USB UHCI Contoller #4
bios:
                       BIOS
bridge:
                       Intel 82801HEM (ICH8M) LPC Interface Controller
                       Intel 82801 Mobile PCI Bridge
                       Intel 82801H (ICH8 Family) PCI Express Port 6
                       Intel 82801H (ICH8 Family) PCI Express Port 4
                       Intel 82801H (ICH8 Family) PCI Express Port 2
                       Intel 82801H (ICH8 Family) PCI Express Port 1
                       Intel Mobile PM965/GM965/GL960 Memory Controller Hub
hub:
                       Broadcom BCM2045B2
                       Linux 2.6.27-7-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.27-7-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-7-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-7-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-7-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.27-7-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.27-7-generic uhci_hcd UHCI Host Controller
memory:
                       Main Memory
firewire controller:
                       Ricoh R5C832 IEEE 1394 Controller
bluetooth:
                       Dell BCM2045
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Ricoh xD-Picture Card Controller
                       Ricoh R5C592 Memory Stick Bus Host Adapter
                       Ricoh R5C843 MMC Host Controller
                       Ricoh R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                       Intel 82801H (ICH8 Family) SMBus Controller
                       OmniVision Laptop Integrated Webcam
```

---

### Post by danzvash on 2009-02-14
Do you know what driver you're using for your Broadcom wireless card?

It will either be ndiswrapper(+Win32 driver), b43 or the proprietary wl.

If it is wl, then you might be experiencing this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/292450](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/292450)

I know that doesn't answer the question, but it's something ;)

---

### Post by Ambush Commander on 2009-02-14
With the new kernels, the panics have gone away.

---

