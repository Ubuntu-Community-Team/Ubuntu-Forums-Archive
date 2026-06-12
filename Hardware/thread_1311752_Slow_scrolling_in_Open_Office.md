---
title: "Slow scrolling in Open Office"
date: 2009-11-02
forum: Hardware
---

### Post by Kognit on 2009-11-02
Hi

I have laptop ASUS K50IJ T3000, Ubuntu 9.10 and i have some slow scrolling problems with my Open Office.
I tried to change some configuration in tools>options>openoffice.org>memory and it doesn't work for me. Is there any problems in graphic driver or it is something with OO.

My lspc:
[HTML]
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
[/HTML]

My lshw:

[HTML] description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2013MiB
     *-cpu
          product: Celeron(R) Dual-Core CPU       T3000  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
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
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:fe400000-fe7fffff memory:d0000000-dfffffff(prefetchable) ioport:dc00(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:fe800000-fe8fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d880(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:d800(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d480(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fe9fbc00-fe9fbfff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:fe9f4000-fe9f7fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 memory:fea00000-feafffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:25:d3:81:7e:0c
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:feaf0000-feafffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:e000(size=4096) memory:feb00000-febfffff
           *-network
                description: Ethernet interface
                product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: b0
                serial: 90:e6:ba:16:49:24
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 multicast=yes
                resources: irq:29 memory:febc0000-febfffff ioport:ec00(size=128)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d400(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d080(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d000(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe9fb800-fe9fbbff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
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
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=32) memory:fe9fb000-fe9fb7ff
[/HTML]

---

### Post by elliottb on 2009-11-12
I'm having possibly a similar problem.  I'm also running 9.10.  OO Presentation for me is a complete disaster.  I've haven't really screwed with it much so I guess I'd better look into the memory thing a little.  

I don't use the presentation software too much, but I did use it months ago on 9.04.  I can't remember any problems for what that's worth.  

Anyway, I'll to update this later.  Currently OO Presentation is not usable. 

Elliott

---

### Post by DapperMe17 on 2009-11-12
Maybe a long shot, but... 

After updating to 9.10, I experienced slow scrolling in my browser.

Changing the default Ubuntu "theme" solved the slow scrolling problem for me.

It might be worth a try!

---

### Post by Kognit on 2009-11-13
> **DapperMe17 said:**
> Maybe a long shot, but... 

After updating to 9.10, I experienced slow scrolling in my browser.

Changing the default Ubuntu "theme" solved the slow scrolling problem for me.

It might be worth a try!

Yes, it is faster a little bit. Thx. What kind of computer you have?

---

### Post by DapperMe17 on 2009-11-13
I have varieties of 'Buntu on many machines.

Remember that Open Office is a very large, "hungry" application. 

More memory = more responsiveness.

On one machine with 512mb RAM, OO opens for me in something like 30 seconds.

---

### Post by Kognit on 2009-11-14
> **DapperMe17 said:**
> I have varieties of 'Buntu on many machines.

Remember that Open Office is a very large, "hungry" application. 

More memory = more responsiveness.

On one machine with 512mb RAM, OO opens for me in something like 30 seconds.

I don't know why is realtively slow on my machine which is laptop 2gb ram, 320 gb HDD, 1,8 duo intel.

---

### Post by elliottb on 2009-11-15
I guess I'll update my response.  I've spend some time fiddling with the "memory" settings in Open Office office presentation.  I can't get it to act normally.  It's really terrible.  I'm definetely a bit of an older computer, and I don't have independent graphics memory.  but I do have 2 gig's of ram.

Is this just a normal thing?  I'll probably try to revert to an older open office if possible.  Currently, it's awful to use.

Anyone know any other tricks?

Elliott

---

### Post by DapperMe17 on 2009-11-15
Plenty of system there.


You might try to uninstall & re-install OO, or download OO firectly from the Open Office web site & install. 


All else equal, it should be plenty responsive with those specs.

As a site note, I couldn´t even get OO to load in Karmic 9.10. I was forced to uninstall & manually download OO from the website.


PS...Don worry about independant graphics, that&#347; not an issue.

---

### Post by elliottb on 2009-11-16
Okay, I'll give that a burn.  Thanks.

I'll update later.

Elliott

---

### Post by Kognit on 2009-11-16
> **DapperMe17 said:**
> Plenty of system there.


You might try to uninstall & re-install OO, or download OO firectly from the Open Office web site & install. 


All else equal, it should be plenty responsive with those specs.

As a site note, I couldn´t even get OO to load in Karmic 9.10. I was forced to uninstall & manually download OO from the website.


PS...Don worry about independant graphics, that&#347; not an issue.

I tried to reinstall but no good. I know that with my specs all should work fine. I think that the problems are graphic drivers - i have Intel's integrated graphic card. 

But i will stay with the Ubuntu anyway - no matter what :)

---

