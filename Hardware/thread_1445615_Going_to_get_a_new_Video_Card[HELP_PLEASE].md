---
title: "Going to get a new Video Card[HELP PLEASE]"
date: 2010-04-02
forum: Hardware
---

### Post by TheNerdAL on 2010-04-02
Okay so I am getting a new video card tommorrow but the one I want isn't at Fry's and my mom wants to go buy it at a store rather than online. So I was wondering if there is a good video card to support desktop effects. 

Here are my specs: 
```
adrian-desktop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 370MiB
     *-cpu
          product: AMD Sempron(tm) Processor 3100+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.12.0
          size: 1800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci:0
          description: Host bridge
          product: 760/M760 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=32
          resources: irq:0 memory:e8000000-ebffffff
        *-pci
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:9000(size=4096) memory:ed000000-ed0fffff memory:e0000000-e7ffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:e0000000-e7ffffff(prefetchable) memory:ed000000-ed01ffff ioport:9000(size=128)
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:a000(size=256) ioport:a400(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:ed113000-ed113fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:ed114000-ed114fff
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:22 memory:ed110000-ed110fff
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:ed111000-ed111fff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:11:d8:44:db:e7
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom ethernet physical
             configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.2.2 latency=32 maxlatency=11 mingnt=52 multicast=yes
             resources: irq:19 ioport:a800(size=256) memory:ed112000-ed112fff memory:20000000-2001ffff(prefetchable)
        *-ide:1
             description: IDE interface
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sis latency=32
             resources: irq:17 ioport:ac00(size=8) ioport:b000(size=4) ioport:b400(size=8) ioport:b800(size=4) ioport:bc00(size=16) ioport:c000(size=128)
        *-communication UNCLAIMED
             description: Communication controller
             product: Conexant Systems, Inc.
             vendor: Conexant Systems, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32
             resources: memory:ed100000-ed10ffff ioport:c400(size=8)
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32
             resources: irq:16 memory:ed115000-ed1157ff ioport:c800(size=128)
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
```

Thanks.

---

### Post by TheNerdAL on 2010-04-02
Bump

---

### Post by 23dornot23d on 2010-04-02
Try this link out ..... its the compatibility hardware list for Linux .....

[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by ubunterooster on 2010-04-02
Search the forums for the cards the store has. Please remeber bumping is not supposed to be more than once per 24hr. Otherwise you could earn an infringement for breaking the rules.

---

### Post by TheNerdAL on 2010-04-02
I want this one: [http://www.frys.com/product/6046258?site=sr:SEARCH:MAIN_RSLT_PG](http://www.frys.com/product/6046258?site=sr:SEARCH:MAIN_RSLT_PG)

---

### Post by ubunterooster on 2010-04-02
GeForce 210? okay. I'll dig around to see if I see any problems...

---

### Post by ubunterooster on 2010-04-02
looks good to me&#8226;

---

### Post by TheNerdAL on 2010-04-02
Thanks! :D

---

### Post by ubunterooster on 2010-04-03
@23ornot: that site is severely lacking in number of hardware devices. :(
@TheNerd: glad to help

---

### Post by 23dornot23d on 2010-04-03
Looks ok ...... on the Nvidia site ..... here is the driver link ......

[http://www.nvidia.com/object/linux_display_ia32_190.42.html](http://www.nvidia.com/object/linux_display_ia32_190.42.html)

its sometimes a good idea to type into Google **Problems Linux** and the name of the Graphics card you are after
just as a rough guide to see what other users have had problems with in the past ..... every system is different
though ...... so always look for the ones similar to your own .........

hope this helps too ..... ;)

---

### Post by TheNerdAL on 2010-04-03
> **23dornot23d said:**
> Looks ok ...... on the Nvidia site ..... here is the driver link ......

[http://www.nvidia.com/object/linux_display_ia32_190.42.html](http://www.nvidia.com/object/linux_display_ia32_190.42.html)

hope this helps too ..... ;)

Sweet, Thanks! :D

---

