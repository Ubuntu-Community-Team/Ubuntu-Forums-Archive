---
title: "Linux not registering all of RAM"
date: 2019-11-30
forum: Hardware
---

### Post by anentree on 2019-11-30
I recently built my first computer and I'm having trouble with Linux registering all the my 16gb RAM. It currently only registers half of that. I read all the forums and still can't find a solution. The BIOS recognizes 16gb, so it seems maybe it's something with Linux? It could be a hardware fault, but all the parts are new.

I tried the RAM slots A1/B1 and A2/B2, and they both gave me the same specs as below.

[ASRock B450M Pro4 motherboard]("https://www.asrock.com/mb/AMD/B450M%20Pro4/") and its [manual]("http://asrock.pc.cdn.bitgravity.com/Manual/B450M%20Pro4.pdf")
Two sticks of [G.SKILL 8GB DDR4 - 3200]("https://www.newegg.com/g-skill-16gb-288-pin-ddr4-sdram/p/N82E16820232181?Item=N82E16820232181") (If you look at the code below, the sticks are running at speeds of 2133 MT/s, which is much slower speeds than advertised.)

The issue is quite aggravating and any deep look into this is much appreciated.

I'm technically running Linux Mint, but it's based off of Ubuntu. 
uname -a
```
Linux 4.15.0-70-generic #79-Ubuntu SMP Tue Nov 12 10:36:11 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

cat /proc/meminfo | grep MemTotal
```
MemTotal:        8093584 kB
```

Which is 8.093584 gB

sudo dmidecode --type memory
```
# dmidecode 3.1Getting SMBIOS data from sysfs.
SMBIOS 3.2.1 present.
# SMBIOS implementations newer than version 3.1.1 are not
# fully supported by this version of dmidecode.


Handle 0x000C, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 128 GB
    Error Information Handle: 0x000B
    Number Of Devices: 4


Handle 0x0013, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x000C
    Error Information Handle: 0x0012
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM 0
    Bank Locator: P0 CHANNEL A
    Type: DDR4
    Type Detail: Synchronous Unbuffered (Unregistered)
    Speed: 2133 MT/s
    Manufacturer: Unknown
    Serial Number: 00000000
    Asset Tag: Not Specified
    Part Number: F4-3200C16-8GVGB
    Rank: 1
    Configured Clock Speed: 2133 MT/s
    Minimum Voltage: 1.2 V
    Maximum Voltage: 1.2 V
    Configured Voltage: 1.2 V


Handle 0x0016, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x000C
    Error Information Handle: 0x0015
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: Unknown
    Set: None
    Locator: DIMM 1
    Bank Locator: P0 CHANNEL A
    Type: Unknown
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Unknown
    Serial Number: Unknown
    Asset Tag: Not Specified
    Part Number: Unknown
    Rank: Unknown
    Configured Clock Speed: Unknown
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: Unknown


Handle 0x0018, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x000C
    Error Information Handle: 0x0017
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM 0
    Bank Locator: P0 CHANNEL B
    Type: DDR4
    Type Detail: Synchronous Unbuffered (Unregistered)
    Speed: 2133 MT/s
    Manufacturer: Unknown
    Serial Number: 00000000
    Asset Tag: Not Specified
    Part Number: F4-3200C16-8GVGB
    Rank: 1
    Configured Clock Speed: 2133 MT/s
    Minimum Voltage: 1.2 V
    Maximum Voltage: 1.2 V
    Configured Voltage: 1.2 V


Handle 0x001B, DMI type 17, 40 bytes
Memory Device
    Array Handle: 0x000C
    Error Information Handle: 0x001A
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: Unknown
    Set: None
    Locator: DIMM 1
    Bank Locator: P0 CHANNEL B
    Type: Unknown
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Unknown
    Serial Number: Unknown
    Asset Tag: Not Specified
    Part Number: Unknown
    Rank: Unknown
    Configured Clock Speed: Unknown
    Minimum Voltage: Unknown
    Maximum Voltage: Unknown
    Configured Voltage: Unknown
```

free -m
```
              total        used        free      shared  buff/cache   available
Mem:           7903        2239        3335         204        2329        5217
Swap:           979           0         979
```

dmesg | grep Memory
```
[    0.000000] Memory: 7945568K/8318612K available (12300K kernel code, 2481K rwdata, 4264K rodata, 2432K init, 2388K bss, 373044K reserved, 0K cma-reserved)
[    0.174223] x86/mm: Memory block size: 128MB
```

df
```
Filesystem                1K-blocks     Used Available Use% Mounted onudev                        4013316        0   4013316   0% /dev
tmpfs                        809360     1492    807868   1% /run
/dev/mapper/mint--vg-root 488960032 34404132 429648332   8% /
tmpfs                       4046792   165308   3881484   5% /dev/shm
tmpfs                          5120        4      5116   1% /run/lock
tmpfs                       4046792        0   4046792   0% /sys/fs/cgroup
/dev/nvme0n1p2               721392   153004    515924  23% /boot
/dev/nvme0n1p1               523248     6232    517016   2% /boot/efi
tmpfs                        809356       20    809336   1% /run/user/1000
/home/.../.Private   488960032 34404132 429648332   8% /home/
```

Full in root;
lshw
```
                    
    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-3.2 dmi-3.2 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=7085C2FE-E434-0000-0000-000000000000
  *-core
       description: Motherboard
       product: B450M Pro4
       vendor: ASRock
       physical id: 0
       serial: M80-CA002100260
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P3.60
          date: 07/31/2019
          size: 64KiB
          capacity: 15MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
             product: F4-3200C16-8GVGB
             vendor: Unknown
             physical id: 0
             serial: 00000000
             slot: DIMM 0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:1
             description: [empty]
             product: Unknown
             vendor: Unknown
             physical id: 1
             serial: Unknown
             slot: DIMM 1
        *-bank:2
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
             product: F4-3200C16-8GVGB
             vendor: Unknown
             physical id: 2
             serial: 00000000
             slot: DIMM 0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:3
             description: [empty]
             product: Unknown
             vendor: Unknown
             physical id: 3
             serial: Unknown
             slot: DIMM 1
     *-cache:0
          description: L1 cache
          physical id: e
          slot: L1 - Cache
          size: 576KiB
          capacity: 576KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: f
          slot: L2 - Cache
          size: 3MiB
          capacity: 3MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 10
          slot: L3 - Cache
          size: 16MiB
          capacity: 16MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: AMD Ryzen 5 2600 Six-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 11
          bus info: cpu@0
          version: AMD Ryzen 5 2600 Six-Core Processor
          serial: Unknown
          slot: AM4
          size: 1549MHz
          capacity: 3900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb hw_pstate sme ssbd ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf xsaveerptr arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov succor smca cpufreq
          configuration: cores=6 enabledcores=6 threads=12
     *-pci:0
          description: Host bridge
          product: Family 17h (Models 00h-0fh) Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Family 17h (Models 00h-0fh) PCIe GPP Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:f7900000-f79fffff
           *-storage
                description: Non-Volatile memory controller
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pciexpress msix msi pm nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:53 memory:f7900000-f7903fff
        *-pci:1
             description: PCI bridge
             product: Family 17h (Models 00h-0fh) PCIe GPP Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=8192) memory:f6000000-f73fffff ioport:e8000000(size=167772160)
           *-usb
                description: USB controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:28 memory:f73a0000-f73a7fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-70-generic xhci-hcd
                   physical id: 0
                   bus info: usb@1
                   logical name: usb1
                   version: 4.15
                   capabilities: usb-2.00
                   configuration: driver=hub slots=10 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: USB Keyboard
                      vendor: Logitech
                      physical id: 5
                      bus info: usb@1:5
                      version: 64.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=90mA speed=2Mbit/s
                 *-usb:1
                      description: Mouse
                      product: USB Optical Mouse
                      vendor: Logitech
                      physical id: 6
                      bus info: usb@1:6
                      version: 72.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-70-generic xhci-hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 4.15
                   capabilities: usb-3.10
                   configuration: driver=hub slots=4 speed=10000Mbit/s
           *-storage
                description: SATA controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:55 memory:f7380000-f739ffff memory:f7300000-f737ffff
           *-pci
                description: PCI bridge
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:31 ioport:e000(size=8192) memory:f6000000-f72fffff ioport:e8000000(size=167772160)
              *-pci:0
                   description: PCI bridge
                   product: Advanced Micro Devices, Inc. [AMD]
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 0
                   bus info: pci@0000:03:00.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:32
              *-pci:1
                   description: PCI bridge
                   product: Advanced Micro Devices, Inc. [AMD]
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 1
                   bus info: pci@0000:03:01.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:34 ioport:f000(size=4096) memory:f7200000-f72fffff
                 *-network
                      description: Ethernet interface
                      product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                      vendor: Realtek Semiconductor Co., Ltd.
                      physical id: 0
                      bus info: pci@0000:05:00.0
                      logical name: enp5s0
                      version: 15
                      serial: 70:85:c2:fe:e4:34
                      size: 1Gbit/s
                      capacity: 1Gbit/s
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                      configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.0.25 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                      resources: irq:33 ioport:f000(size=256) memory:f7204000-f7204fff memory:f7200000-f7203fff
              *-pci:2
                   description: PCI bridge
                   product: Advanced Micro Devices, Inc. [AMD]
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 4
                   bus info: pci@0000:03:04.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:35 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e8000000(size=167772160)
                 *-display
                      description: VGA compatible controller
                      product: GK208B [GeForce GT 710]
                      vendor: NVIDIA Corporation
                      physical id: 0
                      bus info: pci@0000:06:00.0
                      version: a1
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                      configuration: driver=nouveau latency=0
                      resources: irq:59 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
                 *-multimedia
                      description: Audio device
                      product: GK208 HDMI/DP Audio Controller
                      vendor: NVIDIA Corporation
                      physical id: 0.1
                      bus info: pci@0000:06:00.1
                      version: a1
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress bus_master cap_list
                      configuration: driver=snd_hda_intel latency=0
                      resources: irq:33 memory:f7080000-f7083fff
        *-pci:2
             description: PCI bridge
             product: Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 7.1
             bus info: pci@0000:00:07.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:f7500000-f77fffff
           *-generic:0 UNCLAIMED
                description: Non-Essential Instrumentation
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress cap_list
                configuration: latency=0
           *-generic:1
                description: Encryption controller
                product: Family 17h (Models 00h-0fh) Platform Security Processor
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:07:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list
                configuration: driver=ccp latency=0
                resources: irq:67 memory:f7600000-f76fffff memory:f7700000-f7701fff
           *-usb
                description: USB controller
                product: USB 3.0 Host controller
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.3
                bus info: pci@0000:07:00.3
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:44 memory:f7500000-f75fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-70-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 4.15
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-70-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 4.15
                   capabilities: usb-3.00
                   configuration: driver=hub slots=4 speed=5000Mbit/s
        *-pci:3
             description: PCI bridge
             product: Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 memory:f7800000-f78fffff
           *-generic UNCLAIMED
                description: Non-Essential Instrumentation
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress cap_list
                configuration: latency=0
           *-storage
                description: SATA controller
                product: FCH SATA Controller [AHCI mode]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:08:00.2
                version: 51
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress msi ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:57 memory:f7808000-f7808fff
           *-multimedia
                description: Audio device
                product: Family 17h (Models 00h-0fh) HD Audio Controller
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.3
                bus info: pci@0000:08:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:71 memory:f7800000-f7807fff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 59
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 51
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:03.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:04.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:07.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:08.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10a
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:11
          description: Host bridge
          product: Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10b
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10c
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 6
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10d
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 7
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10e
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
```

That's all I got for now. Please help!

Cheers fellows

---

### Post by oldfred on 2019-12-01
Have you updated UEFI? AMD put out fixes for Linux and vendors are releasing updates to UEFI.

What version of Ubuntu?
You probably need 19.10 and maybe newer kernels & drivers.

Vendor updates should be available now as it was July when AMD released to vendors the fixes.
       AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2) 
    
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=1)

---

### Post by rsteinmetz70112 on 2019-12-02
Have you tried using each memory stick alone? It maybe one is DOA.

---

