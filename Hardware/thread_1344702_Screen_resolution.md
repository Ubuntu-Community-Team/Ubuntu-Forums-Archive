---
title: "Screen resolution"
date: 2009-12-03
forum: Hardware
---

### Post by Jeremy07 on 2009-12-03
How do I get a Samsung SyncMaster 931BW to operate at 1440 x900 on 9.10? I have tried setting up xorg.conf file but this does not work - must have it set-up wrong it just causes the computer to blink at a text log-in sign.

 
   **Re: low resolution after 9.10 installation** 
  I used this xorg.conf (got this from a forum)

Content of my xorg.conf - below: and lshw output below.

Help please!
--------------------------------------------------------------
Section "Device"
Identifier "Intel 945G"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "SyncMaster"
Option "DPMS"
Horizsync 30-81
Vertrefresh 60-75
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel 945G"
Monitor "SyncMaster"
Defaultdepth 24
SubSection "Display"
Modes "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

the lshw output is;
               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 939MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          size: 3GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis
          resources: irq:0 memory:f8000000-fbffffff
        *-pci:0
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:c000(size=4096) memory:fdb00000-fdbfffff memory:d0000000-dfffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:d0000000-dfffffff(prefetchable) memory:fdbe0000-fdbfffff ioport:cf00(size=128)
        *-isa
             description: ISA bridge
             product: SiS968 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
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
             capabilities: ide bus_master cap_list
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
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
             resources: irq:20 memory:fdfff000-fdffffff
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
             resources: irq:21 memory:fdffe000-fdffefff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80
             resources: irq:22 memory:fdffd000-fdffdfff
        *-network:0
             description: Ethernet interface
             product: 191 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth1
             version: 02
             serial: 00:1c:25:5a:a1:0a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis190 driverversion=1.3 latency=0 multicast=yes
             resources: irq:19 memory:fdffc000-fdffc07f ioport:fe00(size=128)
        *-ide:1
             description: IDE interface
             product: SATA Controller / IDE mode
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sis latency=64
             resources: irq:17 ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=8) ioport:fa00(size=4) ioport:f900(size=16)
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:e000(size=4096) memory:fda00000-fdafffff ioport:fde00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:d000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
        *-network:1
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: e
             bus info: pci@0000:00:0e.0
             logical name: eth0
             version: 10
             serial: 00:19:cb:d6:f7:6e
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.5 latency=32 maxlatency=64 mingnt=32 multicast=yes
             resources: irq:18 ioport:f600(size=256) memory:fdffb000-fdffb0ff
        *-multimedia
             description: Audio device
             product: Azalia Audio Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=11 mingnt=52
             resources: irq:18 memory:fdff4000-fdff7fff
        *-pci:3
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:b000(size=4096) memory:fd900000-fd9fffff ioport:fd800000(size=1048576)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by Anonymousable on 2009-12-03
Have you tried System>Preferences>Screen Resolution yet?

---

### Post by pjsmetana on 2009-12-03
Use EnvyNG. Download your latest vidcard drivers. Restart. Then System>Preferences>Screen Resolution.

---

### Post by Jeremy07 on 2009-12-03
I have but it does not offer that res and detect monitor does not work

---

### Post by Ganaveh on 2009-12-03
In my PC ,no the Screen Resolution in Preferences.Why?

---

### Post by Jeremy07 on 2009-12-03
Could you please let me have a bit more detail? where to I download the drivers from?

---

### Post by Grenage on 2009-12-03
```
Identifier "Intel 945G"
Driver "intel"
```

For an SiS card?

---

### Post by Anonymousable on 2009-12-03
[edit]

---

### Post by Jeremy07 on 2009-12-03
Yes it is for a SIS card.

---

### Post by Grenage on 2009-12-03
Ok, that config is not for you. You don't have an intel card, and those frequency settings are all wrong!

Give me 5.

---

### Post by Grenage on 2009-12-03
Replace your whole xorg.conf with this:

```
Section "Monitor"
Identifier "Monitor0"
VendorName "Samsung"
ModelName "931BW"
HorizSync 31 - 81
VertRefresh 56 - 75
Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Device"
Identifier "Device0"
VendorName "SiS 771/671"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1400x900"
EndSubSection
EndSection
```

---

### Post by Jeremy07 on 2009-12-17
Thanks for the code - been away for awhile and have only tried it now - I think I am getting closer but when I install it then logout Ubuntu drops to a text login - when I run startx after login I get an error and I think "No screen detected". Any ideas - have checked code carefully but can't find an error.

Thanks for the help

---

### Post by JBAlaska on 2009-12-17
To get really depressed, read this [Thread](http://ubuntuforums.org/showthread.php?t=958967)

For some hope, check this [Link](http://ajoliveira.com/ajoliveira/uk/software/xorg.php)

Either way I don't see you getting 1400x900.

Good luck!

---

### Post by Jeremy07 on 2009-12-17
Thanks - its crazy it works fine as a second monitor on an IBM laptop! So the graphics card/motherboard seems to be the problem. *if  *change these what MB do you suggest?

---

### Post by Grenage on 2009-12-17
I'd personally opt for anything with Nvidia/ATI/Intel graphics.

---

### Post by Jeremy07 on 2009-12-17
Thanks for that

---

### Post by Jeremy07 on 2009-12-18
In the meantime I have tried xorg.conf with the suggested contents - gives "no screen" I then added Driver "sis671" which gives module not found.

Any ideas??

---

### Post by Jeremy07 on 2009-12-21
for those struggling with screen resolutions on SIS hardware this page looks very helpful.

[http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php)

---

