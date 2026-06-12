---
title: "hangcheck_elapsed ERROR, GPU hung"
date: 2011-04-10
forum: Hardware
---

### Post by washakie on 2011-04-10
Hello,

I have just installed Ubuntu 10.10 on an HP 2740p with an Intel i5 processor and an Intel graphics card. All worked perfectly, including Fn keys. I have been using the system for one day now, and I have had this problem twice when the computer should have probably either gone to sleep or displayed the screensaver:

syslog:
Apr 10 19:12:19 olufino kernel: [32137.041680] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung


kern.log:
Apr 10 19:12:19 olufino kernel: [32137.041680] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung

Here is the output of lspci and uname:

uname:
Linux olufino 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

lspci:
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
43:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
44:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
44:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
44:06.2 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev bb)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

and lshw -C display:

  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5058(size=8)


Any ideas?

--john

---

### Post by Pimmetje on 2011-04-28
Still having the issue? I am thinking of also installing ubuntu on my 2740p.

---

### Post by Pimmetje on 2011-04-28
double post ... (error loading page)

---

