---
title: "Random total freeze on 18.04 LTS"
date: 2019-10-02
forum: Hardware
---

### Post by jayz99 on 2019-10-02
Hi All. My system suffers from random, complete freezes from time to time. At times this happens once or twice per day but typically such events are days or weeks apart. 

When the freeze happens, the graphical environment fails to respond. Nothing works. I tried ALT+F2->'r' but the UI just won't respond.

I'm having a hard time identifying what precisely causes this. I had a dig in /var/log and didn't find anything obvious. I've updated the kernel to 5.2.15 and the system is kept up to date.

Any suggestions as to what I should check for and where? [NB. Instinct tells me this is something to do with the GPU...]

System spec:
- Ryzen 5 1600
- Dual GPU: HD5500 (main), RX 570 (driver disabled, passthrough to a Windows VM which runs occasionally)
- 16GB RAM, 8GB permanently allocated to the Windows VM.
- 275 GB SDD, 1TB HDD
```

# uname -a
Linux BlueRidge 5.2.15-050215-generic #201909160732 SMP Mon Sep 16 07:35:27 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

```
# hwinfo --short
cpu:                                                            
                       AMD Ryzen 5 1600 Six-Core Processor, 1375 MHz
                       AMD Ryzen 5 1600 Six-Core Processor, 1375 MHz
                       AMD Ryzen 5 1600 Six-Core Processor, 1375 MHz
                       AMD Ryzen 5 1600 Six-Core Processor, 1375 MHz
                       AMD Ryzen 5 1600 Six-Core Processor, 1375 MHz
                       AMD Ryzen 5 1600 Six-Core Processor, 1375 MHz
                       AMD Ryzen 5 1600 Six-Core Processor, 1375 MHz
                       AMD Ryzen 5 1600 Six-Core Processor, 1375 MHz
                       AMD Ryzen 5 1600 Six-Core Processor, 1400 MHz
                       AMD Ryzen 5 1600 Six-Core Processor, 1375 MHz
                       AMD Ryzen 5 1600 Six-Core Processor, 1480 MHz
                       AMD Ryzen 5 1600 Six-Core Processor, 1384 MHz
keyboard:
  /dev/input/event3    Microsoft Nano Transceiver v1.0 for Bluetooth
mouse:
                       Logitech V220 Cordless Optical Mouse for Notebooks
  /dev/input/mice      Microsoft Nano Transceiver v1.0 for Bluetooth
  /dev/input/mice      Logitech M-UAS144 [LS1 Laser Mouse]
monitor:
                       LG ELECTRONICS LG IPS FULLHD
graphics card:
                       ATI Cedar [Radeon HD 5000/6000/7350/8350 Series]
                       ATI Ellesmere [Radeon RX 470/480]
sound:
                       AMD Audio device
                       ATI Cedar HDMI Audio [Radeon HD 5400/6300/7300 Series]
                       C-Media Electronics CMI8788 [Oxygen HD Audio]
                       ATI Audio device
storage:
                       ASMedia ASM1062 Serial ATA Controller
                       AMD SATA controller
                       AMD FCH SATA Controller [AHCI mode]
network:
  enp37s0              Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
network interface:
  virbr0               Ethernet network interface
  enp37s0              Ethernet network interface
  virbr0-nic           Ethernet network interface
  lo                   Loopback network interface
disk:
  /dev/sdb             SAMSUNG HD080HJ
  /dev/sdc             Crucial_CT275MX3
  /dev/sda             ST1000DM010-2EP1
partition:
  /dev/sdc1            Partition
  /dev/sdc2            Partition
  /dev/sda1            Partition
cdrom:
  /dev/sr0             ATAPI iHAS124   F
usb controller:
                       AMD USB Controller
                       AMD USB Controller
bios:
                       BIOS
bridge:
                       AMD PCI bridge
                       AMD PCI bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD PCI bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD FCH LPC Bridge
                       AMD PCI bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD PCI bridge
                       AMD Host bridge
                       AMD PCI bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD PCI bridge
                       AMD PCI bridge
                       AMD Host bridge
                       AMD PCI bridge
                       AMD PCI bridge
                       AMD Host bridge
                       AMD Host bridge
                       AMD PCI bridge
                       AMD PCI bridge
                       AMD Host bridge
                       ASMedia ASM1083/1085 PCIe to PCI Bridge
hub:
                       Genesys Logic 4-port hub
                       Linux Foundation 2.0 root hub
                       Linux Foundation 3.0 root hub
                       Linux Foundation 2.0 root hub
                       Linux Foundation 3.0 root hub
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Keyboard controller
                       PS/2 Controller
                       AMD IOMMU
                       AMD Non-Essential Instrumentation
                       AMD Encryption controller
                       AMD FCH SMBus Controller
                       AMD Non-Essential Instrumentation
  /dev/ttyS0           16550A
                       Logitech V220 Cordless Optical Mouse for Notebooks
  /dev/input/event7    Microsoft Nano Transceiver v1.0 for Bluetooth
```
```

# lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) I/O Memory Management Unit
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe GPP Bridge
00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe GPP Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe GPP Bridge
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 59)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 7
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X] (rev ef)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 580]
03:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset USB 3.1 xHCI Controller (rev 02)
03:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset SATA Controller (rev 02)
03:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b2 (rev 02)
1d:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
1d:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
1d:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
1d:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
1d:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
1d:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
1e:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 04)
1f:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
24:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
25:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
26:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
26:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300/7300 Series]
27:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 145a
27:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Platform Security Processor
27:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) USB 3.0 Host Controller
28:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 1455
28:00.2 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
28:00.3 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) HD Audio Controller
```

---

### Post by scpatl4now on 2019-10-27
I have had a similar problem.  What kind of MB are you using?  Is your BIOS up to date?  What are you doing when the crash happens?  (I am almost always running Firefox).  Have you run a memory test?  I have an Nvidia card so dont know about AMD, but I also have a Ryzen CPU (1700x)

---

### Post by Autodave on 2019-10-27
Freezes like that *generally* cause me to start checking for RAM issues.  Could be a bad RAM stick, could be overheating of the RAM.  CPU overheat could also cause this: sometimes it tells you that it is shutting down because of that, sometimes it doesn't.

The first thing that I would do is to pull the cover and check for dirt: especially in the CPU cooler.  Are fans all working properly?  Are they clean?  Inlet air grilles clear?  

If you don't see anything obvious, try running a memory test.  Also, leave the cover off to let a little cooler air get in.  A small desk fan blowing onto the interior of the case can help, too.  If it runs OK with the cover off (and a fan blowing air in) then you know that it is an overheating problem.

---

