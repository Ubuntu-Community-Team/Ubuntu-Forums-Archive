---
title: "Hp 2133 with Lubuntu, squiggly lines, and certain odd things"
date: 2014-12-06
forum: Hardware
---

### Post by Aberts10 on 2014-12-06
i have a mini computer, its a HP 2133, i got this out of a box and it has been sitting there for almost 8 years, i turned it on a installed lubuntu with a usb dongle.... everything worked fine....... i have a problem with the graphics though, when i view images or video elements anywhere, they have purple squggily lines and certain GUI elements seem a odd color. For example in skype's contact list it showed a redish orange instead of a yellowish orange like it does normally for me. The graphics driver is Mesa running what appears to be a somewhat recent version: 
[IMG]http://sd.uploads.im/2Enc8.png[/IMG]Any ideas? I dont think it could be the graphics card, this thing was working when put away for ages. im hopping i can save this computer, as i can use it to program and browse the web, or skype. but i also dont want to be spending any money on it, as i could be putting money into other computers that would be more usefull.

---

### Post by mörgæs on 2014-12-06
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Aberts10 on 2014-12-06
```
computer
    description: Notebook
    product: HP 2133 (KX870AT#ABA)
    vendor: Hewlett-Packard
    version: F.02
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=1 family=103C_5336AN sku=KX870AT#ABA uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 3030
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 07.11
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68VGU Ver. F.02
          date: 04/02/2008
          size: 64KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: VIA C7-M Processor 1600MHz
          vendor: CentaurHauls
          physical id: 4
          bus info: cpu@0
          version: 6.13.0
          serial: [REMOVED]
          slot: CPU 1
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 tm nx pni est tm2 xtpr rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en cpufreq
          configuration: cores=1 enabledcores=1 threads=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GiB
        *-bank
             description: DIMM DDR2 Synchronous
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 2GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:f0000000-f7ffffff
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:fbf00000-fcffffff memory:c0000000-cfffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=64 mingnt=2
                resources: memory:c0000000-cfffffff memory:fc000000-fcffffff memory:fbff0000-fbffffff
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:d000(size=4096) memory:fd000000-fdffffff ioport:de000000(size=33554432)
           *-network
                description: Wireless interface
                product: BCM4311 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan1
                version: 02
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=[REMOVED] latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:24 memory:fdffc000-fdffffff
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:e000(size=4096) memory:fe000000-fe9fffff ioport:f8000000(size=50331648)
        *-ide
             description: IDE interface
             product: VT8237/8251 Serial ATA Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=64
             resources: irq:21 ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=16) ioport:c000(size=256)
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:20 ioport:b800(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:b880(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:23 ioport:bc00(size=32)
        *-usb:3
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:21 memory:fbeffc00-fbeffcff
        *-isa
             description: ISA bridge
             product: VT8237S PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht subtractive_decode bus_master cap_list
             resources: memory:fea00000-feafffff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5788 Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:07:03.0
                logical name: eth0
                version: 03
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5788-v3.27 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
                resources: irq:16 memory:feaf0000-feafffff
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8237/8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=128
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT8237A/VT8251 HDA Controller
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=snd_hda_intel latency=0
          resources: irq:17 memory:febfc000-febfffff
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS72201
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: C60A
             serial: [REMOVED]
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=f95eb2ba
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2014-12-06 10:04:08 mount.fstype=ext2 mount.options=rw,relatime mounted=2014-12-06 10:04:08 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 111GiB
                capacity: 111GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: [REMOVED]
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: multi lvm2


```

---

### Post by mörgæs on 2014-12-06
You have a VIA graphics chip. I have not used it myself but it's sometimes discussed here in Ubuntuforums and often people end up using a 12.04 based distro like Bodhi Linux 2.4.

---

### Post by Aberts10 on 2014-12-06
What is the best linux distro for this HP 2133 with GUI and supports the most software, yet runs decently without the graphics issues?

---

### Post by mörgæs on 2014-12-06
Likely Bodhi Linux 2.4. There hasn't been a new release since post #4.

---

### Post by Aberts10 on 2014-12-06
so im guessing i can fix it only by trying diffrent distros?

---

### Post by mörgæs on 2014-12-07
Please read post #4. 
Signing out.

---

