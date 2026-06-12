---
title: "Ubuntu 15.04 cannot detected R9 380x?"
date: 2016-05-22
forum: Hardware
---

### Post by zjhxmjl on 2016-05-22
Hi,guys!
   this is my pc info(who can give me some advance?thanks very much). I'm sure the graphics card is installed correctly!
zjhxmjl@ubuntu:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid
3.19.0-59-generic

zjhxmjl@ubuntu:~$ sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: C61 [GeForce 6150SE nForce 430]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:80000000-8001ffff

zjhxmjl@ubuntu:~$ lspci -vnn | grep -i VGA -A 12
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] [10de:03d0] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:0412]
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
    Capabilities: <access denied>

00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
    Flags: fast devsel
    Capabilities: <access denied>

---

### Post by mörgæs on 2016-05-23
15.04 is old as in 'out of support'.
It's also old in the sense that R9 380x is a new product that can't be expected to work with old software. I suggest that you do a fresh install of 16.04.

If you want help with the 6150 there is also a solution available.

---

### Post by zjhxmjl on 2016-05-23
> **mörgæs said:**
> 15.04 is old as in 'out of support'.
It's also old in the sense that R9 380x is a new product that can't be expected to work with old software. I suggest that you do a fresh install of 16.04.

If you want help with the 6150 there is also a solution available.

OK,thks!I will try 16.04 and give you feedback soon.
BTW,[is this the way of install AMD driver]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD?action=show&redirect=BinaryDriverHowto%2FATI#Manually_installing_Catalyst_12.6")?if i want to detected the R9 380X video card,i must install the dirver first?otherwise i don't install the driver first and ubuntu 16.04 maybe can detected the card?
for this issue, I am confused!

---

### Post by mörgæs on 2016-05-23
For 16.04 there is only one set of AMD drivers available and that's the set which is installed by default. The page to which you linked considers older releases.

---

### Post by zjhxmjl on 2016-05-23
zjhxmjl@ubuntu:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
4.4.0-21-generic
zjhxmjl@ubuntu:~$ lspci -vnn | grep -i VGA -A 12
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] [10de:03d0] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Dell C61 [GeForce 6150SE nForce 430] [1028:0412]
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
    Flags: fast devsel
zjhxmjl@ubuntu:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: C61 [GeForce 6150SE nForce 430]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:20 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:80000000-8001ffff

:(the same!

---

### Post by QIII on 2016-05-24
Hello!

Is this a desktop with a motherboard that has on-board NVIDIA graphics and you have added your AMD R9 380X in a PCIe slot?

If so, have you changed the settings in your BIOS/UEFI to use the PCIe graphics adapter rather than the on-board graphics?  If you have not set the PCIe as primary, it is likely that the PCIe card is being ignored at the BIOS/UEFI level, which is why Ubuntu is not identifying it.

I am running an R9 380X on a Xenial machine.  When Xenial is installing, it detects the R9 380X as suitable to use the AMDGPU driver and installs that rather than the Radeon driver.  Those are your only choices, as 16.04 does not include fglrx and your cannot download and install fglrx from AMD's site to run on 16.04 because fglrx will not run on 16.04's version of X Server.

---

### Post by zjhxmjl on 2016-05-24
> **QIII said:**
> Hello!

Is this a desktop with a motherboard that has on-board NVIDIA graphics and you have added your AMD R9 380X in a PCIe slot?

If so, have you changed the settings in your BIOS/UEFI to use the PCIe graphics adapter rather than the on-board graphics?  If you have not set the PCIe as primary, it is likely that the PCIe card is being ignored at the BIOS/UEFI level, which is why Ubuntu is not identifying it.

I am running an R9 380X on a Xenial machine.  When Xenial is installing, it detects the R9 380X as suitable to use the AMDGPU driver and installs that rather than the Radeon driver.  Those are your only choices, as 16.04 does not include fglrx and your cannot download and install fglrx from AMD's site to run on 16.04 because fglrx will not run on 16.04's version of X Server.

1,"Is this a desktop with a motherboard that has on-board NVIDIA graphics and you have added your AMD R9 380X in a PCIe slot?"
my system is sever version with a motherboard that has on-board NVIDIA graphics and added my AMD R9 380X in a PCIe slot.

2,"If so, have you changed the settings in your BIOS/UEFI to use the PCIe  graphics adapter rather than the on-board graphics?  If you have not set  the PCIe as primary, it is likely that the PCIe card is being ignored  at the BIOS/UEFI level, which is why Ubuntu is not identifying it."
I had checked BIOS,but don't find the option to change.Is my machine too old yet?my pc is dell dimension 2010.

3,"When Xenial is installing, it detects the R9 380X as suitable to use the  AMDGPU driver and installs that rather than the Radeon driver.  Those  are your only choices, as 16.04 does not include fglrx and your cannot  download and install fglrx from AMD's site to run on 16.04 because fglrx  will not run on 16.04's version of X Server"

you mean: i don't download ubuntu 16.04 ? i must download less than 16.04 ?

---

### Post by zjhxmjl on 2016-05-24
[ATTACH=CONFIG]269261[/ATTACH][ATTACH=CONFIG]269262[/ATTACH]

---

### Post by QIII on 2016-05-24
You can run 16.04 with your graphics adaptern. You will just be using the new AMDGPU driver.

Could you provide the motherboard model.  We might be able to find a manual on line and find out what setting changes need to be made.

---

### Post by zjhxmjl on 2016-05-24
> **QIII said:**
> You can run 16.04 with your graphics adaptern. You will just be using the new AMDGPU driver.

Could you provide the motherboard model.  We might be able to find a manual on line and find out what setting changes need to be made.

zjhxmjl@ubuntu:~$ sudo dmidecode -t 2
[sudo] password for zjhxmjl: 
# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.5 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Dell Inc.
    Product Name: 0KGYNX
    Version: A01
    Serial Number: ..CN7360402800JD.

```

zjhxmjl@ubuntu:~$ sudo lshw
ubuntu                    
    description: Computer
    width: 64 bits
    capabilities: smbios-2.5 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1872MiB
     *-cpu
          product: AMD Athlon(tm) II X2 240 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          size: 1600MHz
          capacity: 2800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate vmmcall npt lbrv svm_lock nrip_save cpufreq
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:c000(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:21 ioport:fc00(size=64) ioport:1c00(size=64) ioport:1c40(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02f000-fe02ffff
        *-usbhost
             product: OHCI PCI host controller
             vendor: Linux 4.4.0-21-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 4.04
             capabilities: usb-1.10
             configuration: driver=hub slots=10 speed=12Mbit/s
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 4.4.0-21-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 4.04
             capabilities: usb-2.00
             configuration: driver=hub slots=10 speed=480Mbit/s
           *-usb:0
                description: Mass storage device
                product: Flash Disk
                vendor: USB2.0
                physical id: 3
                bus info: usb@1:3
                logical name: scsi6
                version: 0.00
                serial: 10000000000004CE
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
              *-disk
                   description: SCSI Disk
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/sdb
                   configuration: logicalsectorsize=512 sectorsize=512
           *-usb:1
                description: Mass storage device
                product: DT 101 II
                vendor: Kingston
                physical id: 8
                bus info: usb@1:8
                logical name: scsi7
                version: 1.00
                serial: 001CC0EC347CF071C7E813FC
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
              *-disk
                   description: SCSI Disk
                   physical id: 0.0.0
                   bus info: scsi@7:0.0.0
                   logical name: /dev/sdc
                   size: 3689MiB (3868MB)
                   capabilities: partitioned partitioned:dos
                   configuration: logicalsectorsize=512 sectorsize=512 signature=b078b078
                 *-volume
                      description: Windows FAT volume
                      vendor: MSWIN4.1
                      physical id: 1
                      bus info: scsi@7:0.0.0,1
                      logical name: /dev/sdc1
                      version: FAT32
                      serial: 0000-0000
                      size: 3257MiB
                      capacity: 3281MiB
                      capabilities: primary bootable fat initialized
                      configuration: FATs=2 filesystem=fat label=&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;U&#65533;
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:b000(size=4096) memory:fd800000-fd8fffff memory:fdf00000-fdffffff
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:fe024000-fe027fff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: enp0s7
          version: a2
          serial: a4:ba:db:ed:b4:25
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=10.42.0.54 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:27 memory:fe02d000-fe02dfff ioport:ec00(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:fe02c000-fe02cfff
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c400(size=16) memory:fe02b000-fe02bfff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:a000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25 ioport:9000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26 ioport:8000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:20 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:80000000-8001ffff
     *-pci:4
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: e
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3320418AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: CC45
             serial: 6VMCW4J7
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=3586bfdd
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: 32db35b8-1fe5-41dc-ae93-7f03289b5f5f
                size: 487MiB
                capacity: 487MiB
                capabilities: primary bootable extended_attributes large_files ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2016-05-25 10:11:55 mount.fstype=ext2 mount.options=rw,relatime,block_validity,barrier,user_xattr,acl mounted=2016-05-25 10:00:17 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 297GiB
                capacity: 297GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: gIwqMC-tQTu-Yb56-37Jg-gy6R-EalD-7ONvxQ
                   size: 297GiB
                   capacity: 297GiB
                   capabilities: multi lvm2


```

```
zjhxmjl@ubuntu:~$ lspci
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control


```

this is detail info about my computer :[ATTACH]269275[/ATTACH]

I want to disable the integrated graphics, but the option in BIOS is  disabled by the  dell manufacturer.if flash the BIOS can solve this problem?
.

---

### Post by mörgæs on 2016-05-25
A Bios A04 is available. 

To my surprise Dell does not say what it contains. As far as I remember they used to tell what was changed to help people decide if it was worth it to upgrade. 

Still I think it's worth a shot to upgrade.

---

### Post by zjhxmjl on 2016-05-26
> **mörgæs said:**
> A Bios A04 is available. 

To my surprise Dell does not say what it contains. As far as I remember they used to tell what was changed to help people decide if it was worth it to upgrade. 

Still I think it's worth a shot to upgrade.

Now, i plug it in another pc,it can know it.
```

zjhxmjl@ubuntu:~$ lsmod | grep fglrx
fglrx               12398592  0 
amd_iommu_v2           20480  1 fglrx
zjhxmjl@ubuntu:~$ lspci -vnn | grep -i VGA -A 12
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:6938] (rev f1) (prog-if 00 [VGA controller])
    Subsystem: Tul Corporation / PowerColor Device [148c:2350]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at cfe00000 (64-bit, prefetchable) [size=2M]
    I/O ports at d000 [size=256]
    Memory at feac0000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at feaa0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci

01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:aad8]
    Subsystem: Tul Corporation / PowerColor Device [148c:aad8]


```
but i get another problem,how to install driver for it?i google and find AMD only support driver for  ubuntu 14.04,thks for you advance.
```
zjhxmjl@ubuntu:~$ sudo amdconfig &#8211;initial &#8211;adapter=all
amdconfig: No supported adapters detected

```

---

### Post by mörgæs on 2016-05-27
How did it work using 16.04 in a live boot on the new computer?

---

### Post by zjhxmjl on 2016-05-31
> **mörgæs said:**
> How did it work using 16.04 in a live boot on the new computer?

yes,boot on the new computer  and solved the problem!thks all who give me help!

---

