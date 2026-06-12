---
title: "Ubuntu 17.10 slow graphics performance Intel i915"
date: 2017-11-03
forum: Hardware
---

### Post by theprisoner2 on 2017-11-03
Hi. Can anyone assist? The graphics performance on my desktop is slow. Window switching can be jumpy and menus sometimes take a few seconds to show. I also have audio which sometimes skips, although that could be a standalone issue with Pulseaudio I've had for several Ubuntu releases now. I've read about the i915 intel driver having issues, but I can't seem to find any solutions to sort out the performance. I use the standard GNOME 3 desktop and Wayland, but the same is true of X, and whilst there's been an improvement in performance from 17.04, it's still not right.

My specs are:

INtel Core i3 4010-U @ 1.7 GHz
4 Gig of RAM
256 GB SSD

```
------------

    description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3841MiB
     *-cpu
          product: Intel(R) Core(TM) i3-4010U CPU @ 1.70GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1263MHz
          capacity: 1700MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm cpuid_fault epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts cpufreq
     *-pci
          description: Host bridge
          product: Haswell-ULT DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Haswell-ULT Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff
        *-multimedia:0
             description: Audio device
             product: Haswell-ULT HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:49 memory:f7e14000-f7e17fff
        *-usb:0
             description: USB controller
             product: 8 Series USB xHCI HC
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:42 memory:f7e00000-f7e0ffff
        *-communication
             description: Communication controller
             product: 8 Series HECI #0
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:47 memory:f7e1d000-f7e1d01f
        *-multimedia:1
             description: Audio device
             product: 8 Series HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:f7e10000-f7e13fff
        *-pci:0
             description: PCI bridge
             product: 8 Series PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:df200000-df3fffff ioport:df400000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 8 Series PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:e000(size=4096) memory:f7d00000-f7dfffff
           *-network
                description: Wireless interface
                product: RTL8723AE PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 00
                serial: 48:d2:24:ad:87:ab
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8723ae driverversion=4.13.0-16-generic firmware=N/A ip=192.168.1.70 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:18 ioport:e000(size=256) memory:f7d00000-f7d03fff
        *-pci:2
             description: PCI bridge
             product: 8 Series PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:d000(size=4096) memory:f7c00000-f7cfffff
           *-generic
                description: Unassigned class
                product: RTL8411B PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=rtsx_pci latency=0
                resources: irq:43 memory:f7c15000-f7c15fff memory:f7c00000-f7c0ffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: enp3s0f1
                version: 12
                serial: 00:90:f5:f0:73:ad
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:45 ioport:d000(size=256) memory:f7c14000-f7c14fff memory:f7c10000-f7c13fff
        *-usb:1
             description: USB controller
             product: 8 Series USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7e1b000-f7e1b3ff
        *-isa
             description: ISA bridge
             product: 8 Series LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 8 Series SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7e1a000-f7e1a7ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7e19000-f7e190ff ioport:f040(size=32)

-------------
```

Thanks in advance!

---

### Post by ajgreeny on 2017-11-03
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

You can see in my edit how differently it shows terminal output with all appropriate indentation etc etc.

---

### Post by mörgæs on 2017-11-04
You have a processor focusing on power saving. While it is good for battery life it also limits the performance. 

Have you tried how a lighter environment like Lubuntu 17.10 behaves?

---

### Post by theprisoner2 on 2017-11-04
Hi. Thanks for replying. I've tried the gnome-2-like environment. Same problem. Even though it's a laptop cpu, and geared towards using little power, the desktop environment performance is sub-par to say the least. It's not even a low-spec laptop. It's not as though I'm using it for gaming, just the usual browsing and editing documents.

---

### Post by Yellow Pasque on 2017-11-04
I would try forcing the old intel driver as opposed to generic modesetting.
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Debian-Abandon-Intel-DDX](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Debian-Abandon-Intel-DDX)

---

### Post by theprisoner2 on 2017-11-05
Thanks, Temujin. I'll look into it.

---

