---
title: "HP laptops from $150 to $200 - comments please."
date: 2015-11-30
forum: Hardware
---

### Post by michael-piziak on 2015-11-30
Well, the AMD HP Notebook was sent back, because they slighted me on the memory.
I'm looking to get something Intel this time, because I have been told several times that AMD just isn't keeping up.

Was looking for something like an Intel 2 Core Duo in an HP - I like HP, for between $150 and $200 used.

Came across this one, which is new for $180, but sold out: [http://www.walmart.com/ip/HP-Black-Licorice-15.6-15-R131WM-Laptop-PC-with-Intel-Pentium-N3540-Processor-4GB-Memory-500GB-Hard-Drive-and-Windows-8.1/41122947](http://www.walmart.com/ip/HP-Black-Licorice-15.6-15-R131WM-Laptop-PC-with-Intel-Pentium-N3540-Processor-4GB-Memory-500GB-Hard-Drive-and-Windows-8.1/41122947)

Used one's are available for $250 free shipping, which I could go for $50 more.

Just would like thoughts on either of these vs. an Intel core 2 duo or even an Intel Quad core used laptop.

Comments please on speed of the computer(s) and if Ubuntu 12.04 lts would work well on the ones linked to above.

Michael

---

### Post by sammiev on 2015-11-30
It looks and have the specs of my 8 year old Toshiba but it's running Win8.1

---

### Post by michael-piziak on 2015-11-30
> **sammiev said:**
> It looks and have the specs of my 8 year old Toshiba but it's running Win8.1

This is the type of information I want.  So even though it's new, it's pretty much antiquated the second it leaves the factory.

What are the specs of your 8 year old Toshiba - like processor ?

So, I would be best looking for an Intel Core 2 (or even Quad) processor that is used in the $150 to $200 range, right?

Michael

---

### Post by sammiev on 2015-11-30
> **michael-piziak said:**
> This is the type of information I want.  So even though it's new, it's pretty much antiquated the second it leaves the factory.

What are the specs of your 8 year old Toshiba - like processor ?

So, I would be best looking for an Intel Core 2 (or even Quad) processor that is used in the $150 to $200 range, right?

Michael

I will hook it up in a few hours and post all the specs. It still runs great and is testing Ubuntu-mate 16.04 64bit at this time.

---

### Post by J_Me on 2015-11-30
What about a thinkpad T420 [http://www.ebay.com/bhp/lenovo-t420-used](http://www.ebay.com/bhp/lenovo-t420-used) I bought one used came with windows 7, Kubuntu 1404 worked out of the box wifi drivers and all. Really nice machine.

---

### Post by sammiev on 2015-11-30
Here is my info from a 8 year old Toshiba or older.

```
sam@sam-L500:~$ lshw
WARNING: you should run this program as super-user.
sam-l500                  
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2876MiB
     *-cpu
          product: Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1600MHz
          capacity: 2100MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm cpufreq
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:30 memory:f2800000-f2bfffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f2100000-f21fffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:f2504800-f2504bff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:31 memory:f2500000-f2503fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:f4000000-f5ffffff ioport:f0000000(size=33554432)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:c0000000-c04fffff ioport:f2000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0e:00.0
                logical name: enp14s0
                version: 02
                serial: 00:26:22:3b:16:50
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.16 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:28 ioport:3000(size=256) memory:f2010000-f2010fff memory:f2000000-f200ffff memory:c0000000-c001ffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:f2200000-f22fffff ioport:c0500000(size=2097152)
           *-network
                description: Wireless interface
                product: RTL8191SEvB Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:14:00.0
                logical name: wlp20s0
                version: 10
                serial: 70:1a:04:2a:79:e5
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192se driverversion=4.2.0-19-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:19 ioport:4000(size=256) memory:f2200000-f2203fff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:5000(size=4096) memory:c0700000-c08fffff ioport:c0900000(size=2097152)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18a0(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18c0(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f2504c00-f2504fff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:18e0(size=32) memory:f2504000-f25047ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0b00000-c0b000ff ioport:1c00(size=32)
     *-scsi
          physical id: 2
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-L633C
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: TF01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

---

### Post by michael-piziak on 2015-11-30
The Pentium Core 2 duo, which I think you have, is a heck of a processor - it has aged very well.  My sisters Intel quad core isn't much faster from what I can tell.

The AMD chips; however, are just not keeping up.  The AMD dual processor I just sent back, it lagged and lagged.

Michael

---

### Post by kurt18947 on 2015-12-01
I'm not sure it's accurate to paint all AMD processors with the same brush. The E series AMD processors are for sure not going to keep up with an Intel i3+. They were designed for netbooks, set top boxes, HTPCs etc. where processing power is less important than low power use/low heat. SWMBO has an A6 dual core which doesn't seem to be lacking, given its price point. Will it keep up with a high end i7 or i5? No, but I wouldn't expect it to given that I paid I think $87 for processor and mobo. Without benchmarking I'd say A6 is faster than the 1.5 ghz. Core2 duo I recently sold.  If you really want to increase the 'this thing feel FAST', think about an SSD.

And I too did 2 Ebay Thinkpad refurbs. Both Core i5, one 12" screen - nice 'n' light 'n' portable, one 14" screen. A little over $200 for both of 'em. I did replace the battery on one, it was showing <50% of capacity when fully charged. $16 off Ebay.

---

### Post by michael-piziak on 2015-12-01
Thanks for the information.  This laptop is only going to be used for facebook, youtube, and thunderbird mail 99% of the time.  That AMD I had was simply lagging, but I'm sure you're right that some AMD's aren't lagging.I won't need an SSD drive, besides they are still not economically priced yet.I am willing to go up to $250, and I prefer HP.  I'm sure there are lots of good brands, but HP seems to have better componenets from my own personal experience, and they cost more because of it.I see a  Intel core I5 m560 vpro @ 2.67GHz   used one.  How does that compare to an Intel Core 2 duo ?   It is priced $250

---

