---
title: "Missing CD-ROM on Dell Inspiron 1520 ..."
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by aussie.expat on 2007-08-04
THIS PROBLEM HAS BEEN FIXED
SEE:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/CD_media_not_recognized](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/CD_media_not_recognized)


Hi,

My CDROM is not mounting - and I don even think Ubuntu is finding it to begin with! 

uname -a :

Linux HAL-9000 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

lshw shows:

hal-9000
    description: Portable Computer
    product: Inspiron 1520
    vendor: Dell Inc.
    serial: JFVYCD1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-4600-1056-8059-CAC04F434431
  *-core
       description: Motherboard
       product: 0UW306
       vendor: Dell Inc.
       physical id: 0
       serial: .JFVYCD1.CN4864376P7905.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A00 (05/16/2007)
          size: 64KB
          capacity: 960KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.10
          serial: 0000-06FA-0000-0000-0000-0000
          slot: Microprocessor
          size: 2201MHz
          capacity: 2201MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 4MB
             capacity: 4MB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
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
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: 64T128021EDL3SB2
             vendor: 7F7F7F7F7F510000
             physical id: 0
             serial: 1A014315
             slot: DIMM_A
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: 64T128021EDL3SB2
             vendor: 7F7F7F7F7F510000
             physical id: 1
             serial: 1A014311
             slot: DIMM_B
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 64MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: iomemory:fd000000-fdffffff iomemory:f4000000-f7ffffff iomemory:fa000000-fbffffff ioport:ef00-ef7f irq:16
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:6f20-6f3f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: USB hub
                   product: BCM2045B2
                   vendor: Broadcom
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
                 *-usb:0
                      description: Bluetooth wireless interface
                      product: BCM2045
                      vendor: Broadcom Corp
                      physical id: 1
                      bus info: usb@1:2.1
                      version: 1.00
                      capabilities: bluetooth usb-2.00
                      configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
                 *-usb:1
                      description: Keyboard
                      vendor: Broadcom Corp
                      physical id: 2
                      bus info: usb@1:2.2
                      version: 1.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=0mA speed=12.0MB/s
                 *-usb:2
                      description: Mouse
                      vendor: Broadcom Corp
                      physical id: 3
                      bus info: usb@1:2.3
                      version: 1.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=0mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:6f00-6f1f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:fed1c400-fed1c7ff irq:21
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:febfc000-febfffff irq:20
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0c:00.0
                logical name: eth1
                version: 02
                serial: 00:1b:77:75:40:55
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.105 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
                resources: iomemory:f9fff000-f9ffffff irq:17
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:6f80-6f9f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:6f60-6f7f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:6f40-6f5f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:fed1c000-fed1c3ff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@03:00.0
                logical name: eth0
                version: 02
                serial: 00:19:b9:83:f3:5d
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
                resources: iomemory:f9bfe000-f9bfffff irq:17
           *-firewire
                description: FireWire (IEEE 1394)
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@03:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: iomemory:f9bfd800-f9bfdfff irq:18
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@03:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64
                resources: iomemory:f9bfd400-f9bfd4ff irq:22
           *-system:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@03:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: iomemory:f9bfd500-f9bfd5ff irq:4
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@03:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: iomemory:f9bfd600-f9bfd6ff irq:4
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.4
                bus info: pci@03:01.4
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: iomemory:f9bfd700-f9bfd7ff irq:4
        *-isa
             description: ISA bridge
             product: Mobile LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide UNCLAIMED
             description: IDE interface
             product: Mobile IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:6fa0-6faf irq:7
        *-storage
             description: SATA controller
             product: Mobile SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated scsi-host
             configuration: driver=ahci latency=0
             resources: ioport:6eb0-6eb7 ioport:6eb8-6ebb ioport:6ec0-6ec7 ioport:6ec8-6ecb ioport:6ee0-6eff iomemory:febfb800-febfbfff irq:17
           *-disk
                description: SCSI Disk
                product: ST9160821AS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.CD
                serial: 5MA3HYF5
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux swap / Solaris partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 2055MB
                   capabilities: primary nofs
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 147GB
                   capabilities: primary bootable
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: iomemory:febfb700-febfb7ff ioport:10c0-10df irq:10
  *-battery
       product: DELL GK47976
       vendor: Samsung SDI
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 52000mWh
       configuration: voltage=11.1V


and my fstab shows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=724b0e18-995e-475c-ade9-5a170c6ceeae /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8afc73e4-d69e-484f-9ac3-96826048a931 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


is my CD-ROM even being found?
any ideas how to fix this?

Thanks so much!
Matt

---

### Post by kyphi on 2007-08-04
> is my CD-ROM even being found?

According to the last line in your fstab file: Yes.

What happens when you stick a CD into it?

---

### Post by aussie.expat on 2007-08-04
Nothing happens when I put a CD in - all i was doing is trying to access a data CD. Is that fstab file created and tailored to my system? It&#347; not just a default file?

I&#314;l try a different CD - but according to the fstab it should auto mount to /media/cdrom ?

cheers,
MH

---

### Post by aussie.expat on 2007-08-04
There is nothing at /media/cdrom0

Also, when I try to mount it says ¨mount: special device /dev/hda does not exist¨

Thanks
-Matt

---

### Post by UK-Wobbie on 2007-08-04
> **aussie.expat said:**
> Nothing happens when I put a CD in - all i was doing is trying to access a data CD. Is that fstab file created and tailored to my system? It&#347; not just a default file?

I&#314;l try a different CD - but according to the fstab it should auto mount to /media/cdrom ?

cheers,
MH

It's not trying to access Music files? I no Sometimes on my Ubuntu CD Drives when you put a Game like Worms 2 in it for Wine... It loads as a Music CD! Not a Data CD so i have to right click on it and go to open as file! :)

---

### Post by UK-Wobbie on 2007-08-04
> **aussie.expat said:**
> There is nothing at /media/cdrom0

Also, when I try to mount it says ¨mount: special device /dev/hda does not exist¨

Thanks
-Matt

As the computer got ubuntu on it when you got it from dell? :)

---

### Post by aussie.expat on 2007-08-04
No, I installed Ubuntu myself. Clean install. I wondering if the CD drive has something quirky about it - I could not find a CD drive listed in the diagnostic file I pasted in an earlier post.

Perhaps it&#347; the unclaimed Ricoh device? (Not to be confused with the SD flash disk drive)

Shouldn the CD drive show up in that file?

-Matt

---

### Post by kyphi on 2007-08-04
If you put "dell inspiron 1520" into Search you will find a lot of information why and what things do not work.  So far I have not seen any workarounds but then I have not read it all.

That machine has or had Vista installed and would therefore have AHCI enabled in the BIOS.  Using another option may work.  I will come back on that one.

---

### Post by kyphi on 2007-08-05
Yes, Vista uses AHCI (advanced host controller interface).

In the BIOS, if you go to Advanced, then Drive configuration it might say Configure SATA as 1. IDE, 2. RAID, 3. AHCI.  If it is set to AHCA switch it to IDE and see what happens (or vice versa).

---

### Post by aussie.expat on 2007-08-05
Thanks for the reply. I also came to the same conclusion after reading some about AHCI. The only BIOS options were "AHCI" or "ATA", I tried using ATA but no luck.

This is strange because for a brief time I had SUSE linux running and it found the CD-ROM drive no worries.

Cheers,
-MH

---

### Post by aussie.expat on 2007-08-05
**Problem solved!** All I did was follow the fix from the Dell Linux site:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/CD_media_not_recognized](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/CD_media_not_recognized)

Thanks to everyone who helped.

-Matt

---

