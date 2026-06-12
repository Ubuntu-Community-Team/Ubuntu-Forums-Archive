---
title: "Could Not Write Bytes: Broken Pipe Checking Battery State"
date: 2014-12-07
forum: Hardware
---

### Post by chopra on 2014-12-07
Hi Guys,

I've been getting strange messages on my machine for a while.  It usually happens right after I've logged on or logged off.  I get a black screen, and it says:

Could Not Write Bytes: Broken Pipe 
Checking Battery State

in the upper left corner. Sometimes it gives further details, but that's infrequent enough that I don't remember what they are.
This never caused any problem that I'm aware of, so I've been ignoring it, although the machine is often slow to start up.  It's an hp Notebook, 2000, so maybe it's the age.

Just today, I had locked my screen, and right before I started to unlock it, the computer just spontaniously shut off.  The power button started blinking, and after I pressed it, the machine went back on. I was still logged on.

Then, when I opened up a firefox window, the orange button in the upper left corner used to exit was missing, along with the two grey buttons.  I still closed firefox by closing the single tab, logged off, and logged back on. Now it's back as it should be.

I don't know if these things are related or not. I should mention that I purchased the machine in the United States, where I live, but that currently, I'm in France, and my machine had been plugged into the wall socked via an adapter for a while when this blankout happened.  I know some appliences, like hairdryers, get fried if you use them in europe, and my charger sometimes heats up really fast when it's plugged into a european socket.

Any insights would be appreciated.

Thanks, Chopra

---

### Post by mörgæs on 2014-12-09
First it would be good to check what's printed on the charger. It's obviously built for 115 V 60 Hz but does it accept 230 V 50 Hz as well?

---

### Post by chopra on 2014-12-09
> **mörgæs said:**
> First it would be good to check what's printed on the charger. It's obviously built for 115 V 60 Hz but does it accept 230 V 50 Hz as well?

It's built to accept an electric potential from 100 to 240 V, and a frequency from 50 to 60 Hz.

---

### Post by mörgæs on 2014-12-09
Let's take a look at the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Which release of Buntu are you using?

---

### Post by chopra on 2014-12-10
Thanks for the reply. The output is 458 lines.  You want me to paste the whole thing sanwitched between "["code] and "["/code]?

It's ubuntu 12.05 lts

---

### Post by mörgæs on 2014-12-10
Correct, and please use Preview to verify that the output is readable before posting.

---

### Post by chopra on 2014-12-10
```


computer
    description: Notebook
    product: HP 2000 Notebook PC (D1E85UA#ABA)
    vendor: Hewlett-Packard
    version: 088A120000305910000620100
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=PRE X=MIN sku=D1E85UA#ABA uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 188B
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 69.14
       serial: [REMOVED]
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 0
          version: F.25
          date: 02/21/2013
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 0
             serial: [REMOVED]
             slot: Bottom-Slot 1(top)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: HMT351S6EFR8A-PB
             vendor: Hynix
             physical id: 1
             serial: [REMOVED]
             slot: Bottom-Slot 2(under)
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-cpu
          description: CPU
          product: AMD E1-1200 APU with Radeon(tm) HD Graphics
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 2d
          bus info: cpu@0
          version: AMD E1-1200 APU with Radeon(tm) HD Graphics
          serial: [REMOVED]
          slot: Socket FT1
          size: 1166MHz
          capacity: 1400MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat hw_pstate npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 2e
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 2f
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-pci:0
          description: Host bridge
          product: Family 14h Processor Root Complex
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-display
             description: VGA compatible controller
             product: Wrestler [Radeon HD 7310]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:44 memory:e0000000-efffffff ioport:3000(size=256) memory:f0400000-f043ffff
        *-multimedia:0
             description: Audio device
             product: Wrestler HDMI Audio
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:f0444000-f0447fff
        *-pci:0
             description: PCI bridge
             product: Family 14h Processor Root Port
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:1000(size=4096) memory:f0500000-f06fffff ioport:f0700000(size=2097152)
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:41 ioport:3118(size=8) ioport:3124(size=4) ioport:3110(size=8) ioport:3120(size=4) ioport:3100(size=16) memory:f044c000-f044c7ff
        *-usb:0
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f044b000-f044bfff
        *-usb:1
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f044a000-f044a0ff
        *-usb:2
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f0449000-f0449fff
        *-usb:3
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f0448000-f04480ff
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
            bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:f0440000-f0443fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-pci:2
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:f0300000-f03fffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 05
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
        *-pci:3
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f0200000-f02fffff ioport:f0900000(size=1048576)
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.13.0-40-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f0200000-f027ffff memory:f0900000-f090ffff
        *-pci:4
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 2)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f0100000-f01fffff
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
             version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:42 memory:f0100000-f0100fff
     *-pci:1
          description: Host bridge
          product: Family 12h/14h Processor Function 0
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 43
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 12h/14h Processor Function 1
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 12h/14h Processor Function 2
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 12h/14h Processor Function 3
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
          product: Family 12h/14h Processor Function 4
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 12h/14h Processor Function 6
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 12h/14h Processor Function 5
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 107
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 12h/14h Processor Function 7
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 108
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS54323
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: ES2O
             serial: [REMOVED]
             size: 298GiB (320GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=55461ed1-6f45-40b7-b6ad-1406c489b5e3
           *-volume:0
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: [REMOVED]
                size: 92MiB
                capacity: 93MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 294GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-06-23 19:47:54 filesystem=ext4 lastmountpoint=/ modified=2014-09-14 22:41:51 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-10 14:13:46 state=mounted
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: [REMOVED]
                size: 3682MiB
                capacity: 3682MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT80N
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: R102
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       product: MU06047
       vendor: Conexant (Rockwell)
       physical id: 1
       slot: Primary
       capacity: 47520mWh
       configuration: voltage=10.8V


```

---

### Post by mörgæs on 2014-12-10
With all the problems you have with the present installation I am inclined to suggest a fresh install (not upgrade) of 14.04.1 or 14.10. The hardware is strong so you can choose any of the Buntus.

---

### Post by chopra on 2014-12-14
Hmm,
That might not be doable now.  I've got a lot of stuff on the machine that I don't want to let go of, and transfering and replacing it will take time.
Would it be practical to do a fresh install side-by-side, to see if that fixes the problem?

Chopra

---

### Post by mörgæs on 2014-12-14
Yes, a dual boot is a good idea if you have some empty space.

---

