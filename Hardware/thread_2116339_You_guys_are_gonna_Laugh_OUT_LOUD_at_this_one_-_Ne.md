---
title: "You guys are gonna Laugh OUT LOUD at this one - Need help"
date: 2013-02-15
forum: Hardware
---

### Post by blackblade9x on 2013-02-15
I recently tried to hack my kernel with this software chameleon to get my AMD Phenon II X4 N970 to run Mac OS. Well I fried out my 4400 clock I believe it was HDD in the process(probably due do the fact that Mac OS requires much higher clock speeds) and had to shell out a pretty penny to replace it with a compatible 320gb. I got damn close to getting my mac on my system though, but it failed. I even had it completely installed on a virtual machine once, but it didn't run too pretty on the VmWare.

So after performing the disgusting hackjob on my computer that I did, I tried going back to square one; installing Windows again. Time after time I tried, I just couldn't get windows to install. I'm guessing it has something to do with only god knows what I did to my kernel. So after I had to replace my fried hdd and failing at installing ANY version of Windows, I reinstalled one of my personally favorite operating systems: ubuntu. Because I know ubuntu can be installed on even the most ****** up of computers.

And I found something very interesting when typing uname -a in the terminal today.
Apparently I have a i686 athlon processor! LMAO....

I'd like to fix this so I can use Windows again, so if anyone has any ideas, feel free to share. Thanks.

:lolflag:

---

### Post by lykwydchykyn on 2013-02-15
I think you are confused about what a kernel is.  "Kernel" usually describes a piece of software at the heart of an OS.  There is no way a "hacked kernel" could prevent you from installing an OS, since every OS has its own kernel.

What's more, "uname" does not tell you the make and model of your CPU.   It tells you the general class of processor for which your OS kernel was compiled.  If you want specifics about your processor hardware, try running lshw, dmidecode, or just look at the contents of /proc/cpuinfo.

---

### Post by blackblade9x on 2013-02-15
Ok, the Kernel, BIOS perhaps, I took my OS 101 class about a year ago and I'm a little rusty and yes confused about the technicalities. My point is I think my BIOS or Kernel, I guess it would be the BIOS right? Because that is the closest to the processor itself?  thinks my computer is running a processor that it really isn't. 
The whole idea of the chameleon software I ran when I tried installing the Mac OS was to trick the Mac installation program into thinking it was being installed on an Intel Processor.
I'll run those commands you gave me and see what results come up.

---

### Post by blackblade9x on 2013-02-15
description: Notebook
    product: Aspire 5552 (123456789)
    vendor: Acer
    version: V2.13
    serial: LXR4402263129365171601
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook family=Type1Family sku=123456789 uuid=D1D08936-8E48-11E0-846A-B870F4984EE7
  *-core
       description: Motherboard
       product: JE51_DN
       vendor: Acer
       physical id: 0
       version: Base Board Version
       serial: LXR4402263129365171601
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V2.13
          date: 04/25/2011
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II N970 Quad-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 20
          bus info: cpu@0
          version: 15.5.3
          serial: NotSupport
          slot: Socket S1G4
          size: 800MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0 DISABLED
             description: L1 cache
             physical id: 21
             slot: L1 Cache
             size: 128KiB
             capacity: 512KiB
             capabilities: internal write-through unified
        *-cache:1 DISABLED
             description: L1 cache
             physical id: 22
             slot: L2 Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: internal write-through unified
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1334 MHz (0.7 ns)
             product: EBJ21UE8BFU0-DJ-F
             vendor: Elpida
             physical id: 0
             serial: 2E1D3AA2
             slot: DIMM0
             size: 2GiB
             width: 8 bits
             clock: 1334MHz (0.7ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1334 MHz (0.7 ns)
             product: EBJ21UE8BFU0-DJ-F
             vendor: Elpida
             physical id: 1
             serial: 341D3AA3
             slot: DIMM1
             size: 2GiB
             width: 8 bits
             clock: 1334MHz (0.7ns)
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (int gfx)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:6000(size=4096) memory:f2100000-f22fffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS880M [Mobility Radeon HD 4200 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:18 memory:e0000000-efffffff ioport:6000(size=256) memory:f2200000-f220ffff memory:f2100000-f21fffff
           *-multimedia
                description: Audio device
                product: RS880 HDMI Audio [Radeon HD 4200 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:19 memory:f2210000-f2213fff
        *-pci:1
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=16384) memory:f1100000-f20fffff ioport:f0000000(size=16777216)
           *-network
                description: Ethernet interface
                product: NetLink BCM57780 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: b8:70:f4:98:4e:e7
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 memory:f1100000-f110ffff
        *-pci:2
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:f1000000-f10fffff
           *-network
                description: Wireless interface
                product: BCM43227 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth1
                version: 00
                serial: cc:af:78:72:a3:6e
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.0.104 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:17 memory:f1000000-f1003fff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:42 ioport:7038(size=8) ioport:704c(size=4) ioport:7030(size=8) ioport:7048(size=4) ioport:7010(size=16) memory:f2306000-f23063ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54503
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: GGBO
                serial: TE9B123QKHYYGX
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0007e14c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 816b03ce-946d-4d6d-948e-a695d602a032
                   size: 294GiB
                   capacity: 294GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2013-02-02 19:21:17 filesystem=ext4 lastmountpoint=/ modified=2013-02-02 19:28:20 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2013-02-15 11:27:07 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3834MiB
                   capacity: 3834MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3834MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ8A0AS
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f2305000-f2305fff
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f2306500-f23065ff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f2304000-f2304fff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f2306400-f23064ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f2300000-f2303fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz


Yeah everything looks pretty normal, except it says I have a 32 bit cpu, it's a 64bit! 

Still, I definitely ****** something up.
I mean it's alright cause I can run Windows on VirtualBox just fine but it's still not the same as having the OS installed directly.

---

### Post by tartalo on 2013-02-15
> **blackblade9x said:**
> Yeah everything looks pretty normal, except it says I have a 32 bit cpu, it's a 64bit! 


The info above says that your CPU is 64bits

> *-cpu
description: CPU
product: AMD Phenom(tm) II N970 Quad-Core Processor
vendor: Hynix Semiconductor (Hyundai Electronics)
physical id: 20
bus info: cpu@0
version: 15.5.3
serial: NotSupport
slot: Socket S1G4
size: 800MHz
capacity: 2200MHz
**width: 64 bits**
clock: 200MHz
capabilities: **x86-64** fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
configuration: cores=4 enabledcores=4 threads=4

As far as I know chameleon is just a bootloader:
[https://sites.google.com/site/linkforage/snowleo/chameleon-users-guide](https://sites.google.com/site/linkforage/snowleo/chameleon-users-guide)

Exactly what is the error you get when you try to install Windows?

---

### Post by Mark Phelps on 2013-02-15
> **blackblade9x said:**
> ... and failing at installing ANY version of Windows

We're not mind readers here -- if you want help installing Windows, you need to tell us HOW it failed.  What did you try? What did you see? How far did it get? What errors were displayed?

Also, how is the target drive formatted? Is it blank? Are there any partitions on it already? IF so, what are they?

---

