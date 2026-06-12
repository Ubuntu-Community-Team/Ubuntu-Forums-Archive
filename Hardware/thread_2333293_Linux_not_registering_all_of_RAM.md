---
title: "Linux not registering all of RAM"
date: 2016-08-08
forum: Hardware
---

### Post by swatcher on 2016-08-08
I have been running my system for about six months, just recently was looking at System Monitor and realised that it was only using 7.8 GB of RAM... I have 16GB installed...

So... I read a lot on the forums, but none of the help seemed to fix it.

I could be a hardware fault, but because the parts are new. I'd like to try everything before opting for that.

So I have a [ASRock 970M PRO3 mATX]("http://www.asrock.com/mb/AMD/970M%20Pro3/?cat=Specifications") installed, it takes "Max. capacity of system memory: 64GB..."

I have x2 sticks of [G.Skill 8GB DDR3-2400]("http://www.gskill.com/en/product/f3-2400c10d-8gtx"), the ASRock takes "Supports DDR3 2400+(OC)/2100(OC)/1866(OC)/1800(OC)/1600(OC)/1333/1066 non-ECC..."

My OS is Ubuntu 16.04 64-bit.

... so I took apart my computer, I made sure it was in the right slots.  Happens that if I put it in the wrong spots the computer fails to load,  so that worked well. I have a mATX so I tried everything before I had to  do that... because, the insides of a mATX can be a bit squishy [IMG]https://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG].

So... in accordance will all the other posts on this issue. I have...

cat /proc/meminfo | grep MemTotal
```
Mem Total = 8147216 kb
```
Which is 7.8GB which is what System Monitor is also showing.

sudo dmidecode --type memory
```
# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

Handle 0x000D, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x000F, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM0
    Bank Locator: A1_BANK0
    Type: DDR3
    Type Detail: Synchronous Unbuffered (Unregistered)
    Speed: 1333 MHz
    Manufacturer: Undefined       
    Serial Number: 00000000  
    Asset Tag: A1_AssetTagNum0
    Part Number: F3-2400C10-4GTX   
    Rank: 2
    Configured Clock Speed: 667 MHz

Handle 0x0011, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM1
    Bank Locator: A1_BANK1
    Type: DDR3
    Type Detail: Synchronous Unbuffered (Unregistered)
    Speed: 1333 MHz
    Manufacturer: Undefined       
    Serial Number: 00000000  
    Asset Tag: A1_AssetTagNum1
    Part Number: F3-2400C10-4GTX   
    Rank: 2
    Configured Clock Speed: 667 MHz

Handle 0x0013, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM2
    Bank Locator: A1_BANK2
    Type: Unknown
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: A1_Manufacturer2
    Serial Number: A1_SerNum2
    Asset Tag: A1_AssetTagNum2
    Part Number: Array1_PartNumber2
    Rank: Unknown
    Configured Clock Speed: Unknown

Handle 0x0015, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM3
    Bank Locator: A1_BANK3
    Type: Unknown
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: A1_Manufacturer3
    Serial Number: A1_SerNum3
    Asset Tag: A1_AssetTagNum3
    Part Number: Array1_PartNumber3
    Rank: Unknown
    Configured Clock Speed: Unknown
```

free -m
```
              total        used        free      shared  buff/cache   available
Mem:           7956        1537        5775          65         642        6069
Swap:             0           0           0
```

dmesg | grep Memory
```
[    0.000000] Memory: 7859632K/8360332K available (8394K kernel code, 1282K rwdata, 3944K rodata, 1480K init, 1292K bss, 500700K reserved, 0K cma-reserved)
```

df
```
udev             4020236         0   4020236   0% /dev
tmpfs             814440      9684    804756   2% /run
/dev/sda2      457822440 180024900 254518440  42% /
tmpfs            4072196       676   4071520   1% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            4072196         0   4072196   0% /sys/fs/cgroup
/dev/sda1         523248      3668    519580   1% /boot/efi
tmpfs             814440        64    814376   1% /run/user/1000


```

Full in root;
lshw
```
siren                     
    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: 970M Pro3
       vendor: ASRock
       physical id: 0
       serial: M80-5B020501684
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.30
          date: 09/01/2015
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: AMD FX(tm)-8320 Eight-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD FX(tm)-8320 Eight-Core Processor
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 1400MHz
          capacity: 3500MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold cpufreq
          configuration: cores=8 enabledcores=8 threads=8
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 384KiB
             capacity: 384KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-2400C10-4GTX
             vendor: Undefined
             physical id: 0
             serial: 00000000
             slot: A1_DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-2400C10-4GTX
             vendor: Undefined
             physical id: 1
             serial: 00000000
             slot: A1_DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2016-06-27 17:08+0000X-Generator: Launchpad (build 18115) Synchronous [empty]
             product: Array1_PartNumber2
             vendor: A1_Manufacturer2
             physical id: 2
             serial: A1_SerNum2
             slot: A1_DIMM2
        *-bank:3
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2016-06-27 17:08+0000X-Generator: Launchpad (build 18115) Synchronous [empty]
             product: Array1_PartNumber3
             vendor: A1_Manufacturer3
             physical id: 3
             serial: A1_SerNum3
             slot: A1_DIMM3
     *-pci:0
          description: Host bridge
          product: RD890 PCI to PCI bridge (external gfx0 port B)
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port B)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:e000(size=4096) memory:fd000000-fe0fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GM107 [GeForce GTX 750 Ti]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:31 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fe000000-fe07ffff
           *-multimedia
                description: Audio device
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:29 memory:fe080000-fe083fff
        *-pci:1
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port H)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:fe100000-fe1fffff
           *-usb
                description: USB controller
                product: EJ188/EJ198 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:27 memory:fe100000-fe107fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.4.0-34-generic xhci-hcd
                   physical id: 0
                   bus info: usb@9
                   logical name: usb9
                   version: 4.04
                   capabilities: usb-3.00
                   configuration: driver=hub slots=4 speed=5000Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.4.0-34-generic xhci-hcd
                   physical id: 1
                   bus info: usb@8
                   logical name: usb8
                   version: 4.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:fe20b000-fe20b3ff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe20a000-fe20afff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-34-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
              *-usb:0
                   description: Mouse
                   product: G300s Optical Gaming Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@4:1
                   version: 70.03
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=200mA speed=12Mbit/s
              *-usb:1
                   description: Keyboard
                   product: Razer BlackWidow Tournament Edition
                   vendor: Razer
                   physical id: 4
                   bus info: usb@4:4
                   version: 2.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:fe209000-fe2090ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-34-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
              *-usb
                   description: Video
                   product: HD Pro Webcam C920
                   vendor: Logitech, Inc.
                   physical id: 3
                   bus info: usb@1:3
                   version: 0.11
                   serial: 5AE4331F
                   capabilities: usb-2.00
                   configuration: driver=snd-usb-audio maxpower=500mA speed=480Mbit/s
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe208000-fe208fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-34-generic ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:fe207000-fe2070ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-34-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:fe200000-fe203fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe206000-fe206fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-34-generic ohci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-pci:3
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:4
             description: PCI bridge
             product: SB900 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15.3
             bus info: pci@0000:00:15.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) ioport:d2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: enp5s0
                version: 06
                serial: d0:50:99:99:2f:c0
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:28 ioport:d000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:fe205000-fe205fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-34-generic ohci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=4 speed=12Mbit/s
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:fe204000-fe2040ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-34-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
     *-pci:1
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: OCZ-TRION100
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: 11.1
             serial: 75DB61GVKMFX
             size: 447GiB (480GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=4afb0329-ecd2-4aab-8fcf-7b2ab56541d4 logicalsectorsize=512 sectorsize=512
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@3:0.0.0,1
                version: FAT32
                serial: 0bd9-08c8
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI System Partition
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: d0eef1e3-e9e4-476e-b7f1-9ace0f912583
                size: 443GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-06-11 20:41:09 filesystem=ext4 lastmountpoint=/ modified=2016-08-09 11:28:53 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-08-09 11:28:54 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@3:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: f3b5dd41-f50d-40ed-8fd2-ce237c030dfa
                size: 2998MiB
                capacity: 2998MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
```


Besides that, I have no clue rather than just reading and following instructions -.-.

Please help :).

Thanks in advance...

Edit: So far, changing their slots hasnt worked. Are currently in the correct A2/B2 slots as written DDR3 2400 should be located in.

Edit: Checked physical RAM's sticker, says each stick is 8GB and purchased from a company not an individual seller. My invoice says their code is F3-2400C10D-8GTX. The other two items received work well, but I'll email them and see what happens.

---

### Post by CatKiller on 2016-08-09
The first thing to do is to check the memory status in the BIOS. You may need to configure them differently to have them show up.

Memory modules are often "double-sided," where they are pairs of banks of memory chips. Systems only seeing half of a stick of RAM is an old old problem.

It is usual for Linux to report less memory available than the size of the physical memory that exists; it needs some for itself, and so that memory is no longer available for anything else.

Edit: your output is showing that it's only found half of the chips in the modules in banks 0 & 1, and it's running them at half speed, and it's not detected any modules installed in banks 2 & 3. That definitely looks like a hardware configuration problem or an incompatibility between your RAM modules and your motherboard's memory controller.

Edit: the website you linked for the RAM specifications confirms that each module is arranged as 2×4 GB. Some motherboards require that the slots are filled in particular ways, say banks 0 and 2 for one configuration. Your motherboard's manual should tell you more.

Edit: from your motherboard's manual: > Please install the memory module into DDR3_A2 and DDR3_B2 slots for the first priority.
If you adopt DDR3 2400/2100 memory modules on this motherboard, it is recom-
mended to install them on DDR3_A2 and DDR3_B2 slots.

Also, crucial.com's parts checker is a very useful tool for establishing memory module compatibility.

Edit: you say you should have 32 GB installed, but two of the sticks you linked to would be 16 GB.

---

### Post by Yellow Pasque on 2016-08-09
> Part Number: F3-2400C10-4GTX

You've got two 4GB sticks. I don't see an issue here, other then you're confused about what you bought, or perhaps received the wrong product.

---

### Post by CatKiller on 2016-08-09
> **Temüjin said:**
> You've got two 4GB sticks. I don't see an issue here, other then you're confused about what you bought, or perhaps received the wrong product.

Good spot. It's so hard to read the output on a phone.

---

### Post by swatcher on 2016-08-09
> **Temüjin said:**
> You've got two 4GB sticks. I don't see an issue  here, other then you're confused about what you bought, or perhaps  received the wrong product.

I bought them from a reputable wholesaler. The stickers on the side say that they're F3-2400C10D. I emailed them to ask. But still doesnt explain why their being used at 1333 even if they are F3-2400C10-4GTX.

But you are right regardless, the sticks are 4 GB. I took one out and just loaded one. Its coming up saying that they are 4gb each.

Which is weird, because the motherboard loaded them both even though they were in the wrong spot... O.o.

---

### Post by swatcher on 2016-08-09
> **CatKiller said:**
> The first thing to do is to check the memory status in the BIOS. You may need to configure them differently to have them show up.

Memory modules are often "double-sided," where they are pairs of banks of memory chips. Systems only seeing half of a stick of RAM is an old old problem.

It is usual for Linux to report less memory available than the size of the physical memory that exists; it needs some for itself, and so that memory is no longer available for anything else.

Edit: your output is showing that it's only found half of the chips in the modules in banks 0 & 1, and it's running them at half speed, and it's not detected any modules installed in banks 2 & 3. That definitely looks like a hardware configuration problem or an incompatibility between your RAM modules and your motherboard's memory controller.

Edit: the website you linked for the RAM specifications confirms that each module is arranged as 2×4 GB. Some motherboards require that the slots are filled in particular ways, say banks 0 and 2 for one configuration. Your motherboard's manual should tell you more.

Edit: from your motherboard's manual: 

Also, crucial.com's parts checker is a very useful tool for establishing memory module compatibility.

Edit: you say you should have 32 GB installed, but two of the sticks you linked to would be 16 GB.

I got super excited when I read this.

Because they were put in two slots next to each other, my bad for not noting that in the manual! Ffs. Super excited, pulled them out, reslotted them in Slot 1/3. Still not reading them. I took them out, did the other, Slot 2/4. Still only registering 7.8GiB.

Yea totally assumed they were 16 GB, but it "makes up" 16GB, yea they  are two 8s, memory, even the link i had saved it as when I purchased  them correctly said 8 :). I didnt recheck their ram usage, I went from memory. I half remembered correctly, that I had purchased "16 gigs" just, they are combined not separated into that amount.

> **CatKiller said:**
> Also, crucial.com's parts checker is a very useful tool for establishing memory module compatibility.
[https://au.pcpartpicker.com/list/](https://au.pcpartpicker.com/list/) is what i used yea... to determine compatibility.

---

### Post by swatcher on 2016-08-09
> **CatKiller said:**
> "... and it's running them at half speed"

sudo dmidecode --type memory
```
# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

Handle 0x000D, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x000F, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM0
    Bank Locator: A1_BANK0
    Type: Unknown
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: A1_Manufacturer0
    Serial Number: A1_SerNum0
    Asset Tag: A1_AssetTagNum0
    Part Number: Array1_PartNumber0
    Rank: Unknown
    Configured Clock Speed: Unknown

Handle 0x0011, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM1
    Bank Locator: A1_BANK1
    Type: DDR3
    Type Detail: Synchronous Unbuffered (Unregistered)
    Speed: 1333 MHz
    Manufacturer: Undefined       
    Serial Number: 00000000  
    Asset Tag: A1_AssetTagNum1
    Part Number: F3-2400C10-4GTX   
    Rank: 2
    Configured Clock Speed: 667 MHz

Handle 0x0013, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM2
    Bank Locator: A1_BANK2
    Type: Unknown
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: A1_Manufacturer2
    Serial Number: A1_SerNum2
    Asset Tag: A1_AssetTagNum2
    Part Number: Array1_PartNumber2
    Rank: Unknown
    Configured Clock Speed: Unknown

Handle 0x0015, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: A1_DIMM3
    Bank Locator: A1_BANK3
    Type: DDR3
    Type Detail: Synchronous Unbuffered (Unregistered)
    Speed: 1333 MHz
    Manufacturer: Undefined       
    Serial Number: 00000000  
    Asset Tag: A1_AssetTagNum3
    Part Number: F3-2400C10-4GTX   
    Rank: 2
    Configured Clock Speed: 667 MHz
```

Yea it says it here right. This is the dmidecode after putting the RAM into the A2/B2 proper slots that it says are right for DDR3.

So A2 and B2 on that list are both saying their running at 1333... but the actual ram is 2400... so even though its saying on it, the parts number is 4GTX, it still says 2400 in that same sentence. So still makes no sense, even if they are 4GB sticks (which I dont think they are), for them to be running so slowly... if thats where I'm reading correctly that you are taking that data from O.o :).

---

### Post by swatcher on 2016-08-09
So yeah... I sent an angry email to the distributor and asked for a refund. Thanks for the help guys, much appreciated.

I hope for the company's sake that someone else put the wrong stickers on it... because now... im thinking of submitting an angry consumer report to the ACCC about it (who will investigate the companies wrong doing)... -.-. Sigh...

---

### Post by CatKiller on 2016-08-09
A memory bus speed of 1333 MHz would be right for DDR3-2400: [https://en.wikipedia.org/wiki/DDR3_SDRAM](https://en.wikipedia.org/wiki/DDR3_SDRAM)

It's this part > Configured Clock Speed: 667 MHz that makes me think you might still need to check the BIOS settings. I could be wrong, though.

---

### Post by Yellow Pasque on 2016-08-10
It's **Double** Data Rate , so 1333 * 2 = 2666

As for 7.8 vs. 8GB, a little bit of the addressing range is probably being used for hardware. It's nothing to get in a twist over. Double check exactly what you ordered before shooting off angry e-mails and don't whip out the outrage card before it's absolutely necessary.

> It's this part    Configured Clock Speed: 667 MHz  that makes me think you might still need to check the BIOS settings. I could be wrong, though.

I believe that is just the conservative SPD setting that the RAM comes configured with for compatibility purposes. Motherboards that support XMP (which the OP's does) should clock the RAM at the max rated speed without tweaking. As for the slot placement, it probably doesn't matter except for purposes of dual-channel operation.

Again, I don't see an issue here except consumer confusion.

---

