---
title: "souping up a 2005 Packard-Bell PC with AMD 64 Athlon"
date: 2019-08-13
forum: Hardware
---

### Post by shantiq on 2019-08-13
ok so I have a 2005 Packard-Bell PC with AMD 64 Athlon
I have entered all the specs below    lspcu and lshw   also dmidecode


I also add photos of chip


[[IMG]https://i.postimg.cc/Js7r25Nk/IMG-6393.jpg[/IMG]]("https://postimg.cc/Js7r25Nk")


[[IMG]https://i.postimg.cc/nMvnVPTm/IMG-6394.jpg[/IMG]]("https://postimg.cc/nMvnVPTm")




AND MY QUESTION having added all the Ram i could which CPU chip [if that is the correct terms] could i place in this computer to soup it up a bit/a lot.  
Ideally I would like the chip which is the highest this Motherboard can handle


I am looking for advice from someone who knows these AMD chips.  Can my motherboard handle dual-core?    etc etc


You probably realize I know little about all this but i am keen to try with supporting advice




Thanking you ahead of time




shan


```
bash-4.3# lscpuArchitecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
Vendor ID:             AuthenticAMD
CPU family:            15
Model:                 47
Model name:            AMD Athlon(tm) 64 Processor 3400+
Stepping:              2
CPU MHz:               1800.000
CPU max MHz:           2200.0000
CPU min MHz:           1000.0000
BogoMIPS:              3581.47
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good nopl extd_apicid pni lahf_lm 3dnowprefetch vmmcall



```

dmidecode

```
Handle 0x0004, DMI type 4, 35 bytesProcessor Information
    Socket Designation: CPU 1
    Type: Central Processor
    Family: Athlon 64
    Manufacturer: AMD              
    ID: F2 0F 02 00 FF FB 8B 07
    Signature: Family 15, Model 47, Stepping 2
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
    Version: AMD Athlon(tm) 64 Processor 3400+                   
    Voltage: 3.3 V 2.9 V
    External Clock: 200 MHz
    Max Speed: 2200 MHz
    Current Speed: 2200 MHz
    Status: Populated, Enabled
    Upgrade: Socket 939
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.



```

---

### Post by shantiq on 2019-08-13
lshw

```







bash-4.3# lshw
shan                        
    description: Desktop Computer
    product: 00000000000000000000000 (To Be Filled By O.E.M.)
    vendor: Packard Bell NEC
    version: PB34225301
    serial: 049652320227
    width: 4294967295 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=549D0B9A-BE69-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012
          date: 09/06/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3400+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1GHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni lahf_lm 3dnowprefetch vmmcall cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal varies data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS4xx PCI Express Port [ext gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:6000(size=4096) memory:ff100000-ff1fffff ioport:bff00000(size=536870912)
           *-display
                description: VGA compatible controller
                product: Caicos PRO [Radeon HD 7450]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:c0000000-cfffffff memory:ff1e0000-ff1fffff ioport:6800(size=256) memory:ff1c0000-ff1dffff
           *-multimedia
                description: Audio device
                product: Caicos HDMI Audio [Radeon HD 6400 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:19 memory:ff1bc000-ff1bffff
        *-pci:1
             description: PCI bridge
             product: RC4xx/RS4xx PCI Express Port 3
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:7000(size=4096) memory:ff200000-ff2fffff
           *-network
                description: Wireless interface
                product: RTL8192EE PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: 50:3e:aa:eb:e7:41
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ee driverversion=4.4.14 firmware=N/A ip=192.168.0.16 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 ioport:7800(size=256) memory:ff2fc000-ff2fffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:ff6ffc00-ff6ffdff memory:ff600000-ff67ffff
        *-ide:1
             description: IDE interface
             product: IXP SB4x0 Serial ATA Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:ff6ff800-ff6ff9ff memory:ff580000-ff5fffff
        *-usb:0
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:ff6fe000-ff6fefff
        *-usb:1
             description: USB controller
             product: IXP SB4x0 USB Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:ff6fd000-ff6fdfff
        *-usb:2
             description: USB controller
             product: IXP SB4x0 USB2 Host Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:ff6fc000-ff6fcfff
        *-serial
             description: SMBus
             product: IXP SB4x0 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:be000000-be0003ff
        *-ide:2
             description: IDE interface
             product: IXP SB4x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-isa
             description: ISA bridge
             product: IXP SB4x0 PCI-ISA Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: IXP SB4x0 PCI-PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:8000(size=4096) memory:ff300000-ff3fffff
           *-network:0
                description: Ethernet interface
                product: RTL8169 PCI Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:03:01.0
                logical name: eth1
                version: 10
                serial: 00:0a:cd:26:64:71
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:9 ioport:8800(size=256) memory:ff3ffc00-ff3ffcff memory:ff3c0000-ff3dffff
           *-network:1
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:0d:bb
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 ioport:8400(size=256) memory:ff3ff800-ff3ff8ff memory:ff3e0000-ff3effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:03:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:9 memory:ff3ff000-ff3ff7ff ioport:8c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:ff6ff400-ff6ff4ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@1:1
       logical name: eth2
       serial: 4a:74:6e:b9:b0:98
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth link=no multicast=yes
```

---

### Post by crip720 on 2019-08-13
Quick google search for motherboard came up with this that might help.  [https://forums.tomshardware.com/threads/nec-orion-ms-7168-v1-0-fastest-processor-upgrade.423899/](https://forums.tomshardware.com/threads/nec-orion-ms-7168-v1-0-fastest-processor-upgrade.423899/)

---

### Post by shantiq on 2019-08-13
Thanx crip it does look helpful

found this [overall info ]("https://www.howtogeek.com/348571/how-to-upgrade-and-install-a-new-cpu-or-motherboard-or-both/")article
found [URL="http://www.cpu-world.com/Sockets/Socket%20939.html"]this too

[/URL]

since there is no specs anywhere i can see   based  on info here

> **Supported processors**

[COLOR=#000000][FONT=verdana][Sempron / Sempron 64]("http://www.cpu-world.com/CPUs/K8/TYPE-Sempron%2064.html") (1.8 GHz - 2 GHz, or 3000+ - 3500+)
[Athlon 64]("http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064.html") (1.8 GHz - 2.4 GHz, or 3000+ - 4000+)
[Athlon 64 X2]("http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064%20X2.html") (2 GHz - 2.4 GHz, or 3800+ - 4800+)
[Athlon 64 FX]("http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064%20FX.html") (FX-53 - FX-60)
[Opteron]("http://www.cpu-world.com/CPUs/K8/TYPE-Opteron.html") (1.8 GHz - 3 GHz, or model 144 - model 156)
[/FONT][/COLOR]
[Dual-Core Opteron]("http://www.cpu-world.com/CPUs/K8/TYPE-Dual-Core%20Opteron.html")[COLOR=#000000][FONT=verdana] (1.8 GHz - 2.6 GHz, or model 165 - model 185)[/FONT][/COLOR]

will plump for an [Athlon 64 X2]("http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064%20X2.html") and see what happens since they cost under a tenner


Will report later :]   if anyone spots any contraindication plz say

---

### Post by TheFu on 2019-08-13
[https://www.cpubenchmark.net/cpu.php?cpu=AMD+Athlon+64+3400%2B&id=69](https://www.cpubenchmark.net/cpu.php?cpu=AMD+Athlon+64+3400%2B&id=69)
540 passmarks.  Check the passmarks of the replacement CPU and decide if it is worth it to you.

---

### Post by shantiq on 2019-08-13
Thanx TheFu
i think i understand these charts
Those Ryzen chips have high performance it seems
Thing is i just want to change chip so not sure those would work without also upgrading fan and maybe also ram
i have ordered an X2 to start see how that improves speed of processes
if good will maybe see if a Ryzen is feasible

thanx for input

i fear somehow that these here are my limits with this Motherboard

[COLOR=#800000]**Supported processors**[/COLOR]

[COLOR=#000000][FONT=verdana][Sempron / Sempron 64]("http://www.cpu-world.com/CPUs/K8/TYPE-Sempron%2064.html") (1.8 GHz - 2 GHz, or 3000+ - 3500+)
[Athlon 64]("http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064.html") (1.8 GHz - 2.4 GHz, or 3000+ - 4000+)
[Athlon 64 X2]("http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064%20X2.html") (2 GHz - 2.4 GHz, or 3800+ - 4800+)
[Athlon 64 FX]("http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064%20FX.html") (FX-53 - FX-60)
[Opteron]("http://www.cpu-world.com/CPUs/K8/TYPE-Opteron.html") (1.8 GHz - 3 GHz, or model 144 - model 156)
[/FONT][/COLOR]
[Dual-Core Opteron]("http://www.cpu-world.com/CPUs/K8/TYPE-Dual-Core%20Opteron.html")[COLOR=#000000][FONT=verdana] (1.8 GHz - 2.6 GHz, or model 165 - model 185)[/FONT][/COLOR]

---

### Post by shantiq on 2019-08-16
so in the end went from &#10122; to &#10123;   [you are limited by the type of card slot so you cannot leap that far ahead without also changing CPU cooler Fan & possibly Power Unit] and although it seems like not much of an upgrade it still feels a lot faster especially when using FFox
It cost me £22 for the card and £1,20 for a syringe of Thermal Grease to place between card and Fan  [a must we are told]


To that I must add the £7 I spent on an AM2 card which does not fit in Socket 939 "Processors designed for **Sockets** 754, **939**, and 940 include DDR memory controllers and are not pin **compatible** with **Socket AM2**. **Sockets 939**, 940, and **AM2** support HyperTransport v2.0"; 

So all in all well worth it!   Cannot see any speed difference between this and my 3-year old Acer although it says the Acer >> i3-6100 CPU @ 3,70GHz

+   the machine with SSD and new chip is totally silent  ,,,,,    2005 souped up :]

Recently added new Wifi card and Graphic card too so my 2005 toy plays 1080 HD without blinking ...

&#10122;
    Version: AMD Athlon(tm) 64 [COLOR=#800000]Processor 3400+                   [/COLOR]
    Voltage: 3.3 V 2.9 V
    External Clock: 200 MHz
    Max Speed: 2200 MHz
    Current Speed: 2200 MHz
    Status: Populated, Enabled
    Upgrade: Socket 939
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.


=======================================


&#10123;

    Version: AMD Athlon(tm) 64 [COLOR=#800000]X2 Dual Core Processor 4800+[/COLOR]      
    Voltage: 3.3 V 2.9 V
    External Clock: 200 MHz
    Max Speed: 2400 MHz
    Current Speed: 2400 MHz
    Status: Populated, Enabled
    Upgrade: Socket 939
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007


========================================

---

