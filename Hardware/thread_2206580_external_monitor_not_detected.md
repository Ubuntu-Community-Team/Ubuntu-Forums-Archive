---
title: "external monitor not detected"
date: 2014-02-19
forum: Hardware
---

### Post by sks24 on 2014-02-19
I have a Dell XPS L702x running 12.04, but it won't detect my Asus PA248Q external monitor.  I did try the software listed here: [https://launchpad.net/~hughescih/+archive/ppa](https://launchpad.net/~hughescih/+archive/ppa).  On first reboot there was a notification on the external monitor that the drive wasn't ready (I think, I not sure), but the laptop continued to boot normally: I got the sign-in screen, I logged in, but still the external monitor wasn't detected.  On further reboots that didn't happen again.  This is a dual-boot setup, and the external monitor works fine in the Win 7 partition.   

```
Dell-System-XPS-L702X:~$ lshw
WARNING: you should run this program as super-user.
-dell-system-xps-l702x
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7879MiB
     *-cpu
          product: Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:f0000000-f20fffff ioport:c0000000(size=335544320)
           *-display
                description: VGA compatible controller
                product: GF106M [GeForce GT 550M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:f0000000-f1ffffff memory:c0000000-cfffffff memory:d0000000-d3ffffff ioport:4000(size=128) memory:f2000000-f207ffff
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:54 memory:f2400000-f27fffff memory:e0000000-efffffff ioport:5000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:53 memory:f3c05000-f3c0500f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f3c0a000-f3c0a3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:56 memory:f3c00000-f3c03fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f3b00000-f3bfffff
           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6230 [Rainbow Peak]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 34
                serial: 88:53:2e:30:b6:b9
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-36-generic firmware=18.168.6.1 ip=192.168.1.71 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:55 memory:f3b00000-f3b01fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:f3a00000-f3afffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:f3a00000-f3a01fff
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:f3100000-f39fffff ioport:f2800000(size=8388608)
        *-pci:5
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) ioport:f3000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0a:00.0
                logical name: eth0
                version: 06
                serial: 14:fe:b5:c1:fb:16
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:51 ioport:2000(size=256) memory:f3004000-f3004fff memory:f3000000-f3003fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f3c09000-f3c093ff
        *-isa
             description: ISA bridge
             product: HM67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:52 ioport:5088(size=8) ioport:5094(size=4) ioport:5080(size=8) ioport:5090(size=4) ioport:5060(size=32) memory:f3c08000-f3c087ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f3c04000-f3c040ff ioport:efa0(size=32)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
Dell-System-XPS-L702X:~$ 

```

---

### Post by alex169 on 2014-03-13
I have the same problem. I managed to get the laptop screen working by following the instructions [here]("http://www.cmdematos.com/2011/10/ubuntu-1110-oneric-on-dell-xps17-l702x.html") but I still can't get the second monitor to display, even after using these commands to try and add it manually:

alex@Dell-XPS-L702X:/$ xrandr -q
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 32767 x 32767
LVDS1 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1600x900       60.0*+
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
alex@Dell-XPS-L702X:/$ cvt 1680 1050
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
alex@Dell-XPS-L702X:/$ xrandr --addmode DP1 ^C
alex@Dell-XPS-L702X:/$ xrandr --addmode DP1 1680x1050_60.00
xrandr: cannot find mode "1680x1050_60.00"
alex@Dell-XPS-L702X:/$ xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
alex@Dell-XPS-L702X:/$ xrandr --addmode DP1 1680x1050_60.00alex@Dell-XPS-L702X:/$ xrandr --output DP1 --mode 1680x1050_60.00 --left-of LVDS1
** xrandr: Configure crtc 1 failed**

I've read various things around the web (which I didn't really know if they applied to me or not TBH) that seem to indicate that it just doesn't work. After two days of searching and hacking around, I gave up, moved my laptop in front of me and my second monitor to the right and switched the monitor off and just use the single screen for Linux. It sucks but that's life. Until the hardware support improves, I can't switch full-time to Ubuntu but I might use it for some development work.

---

### Post by sks24 on 2014-03-14
Thanks for chiming in Alex.  I've made my peace with it, too.  Not a huge deal, as the 17 inch screen and resolution on the L702X should make video editing easy.  That's what I'm going to use it for.  I mostly live in a Chromebook now.    
Best,
Scott

---

