---
title: "My HP Pavilion g6 laptop cpu temp goes over 90C. ubuntu 12.04"
date: 2013-08-11
forum: Hardware
---

### Post by mujjingun on 2013-08-11
It is so hot that when you touch it it [COLOR=#ff0000]burns.[/COLOR]
adding " acpi_osi=Linux " does not work.
when you boot it, it only takes 2 minutes to reach 80C.

lshw command:
```

ubuntu                    
    description: Notebook
    product: HP Pavilion g6 Notebook PC (B8M29PA#AB1)
    vendor: Hewlett-Packard
    version: 0791100000205610000620100
    serial: 5CD22058LD
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=PAV X=Null sku=B8M29PA#AB1 uuid=35434432-3230-3538-4C44-A0B3CC794123
  *-core
       description: Motherboard
       product: 183E
       vendor: Hewlett-Packard
       physical id: 0
       version: 56.16
       serial: PCSCN012C1VBJ4
       slot: Type2 - Board Chassis Location
     *-memory
          description: System Memory
          physical id: 0
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: M471B5273DH0-CK0
             vendor: Samsung
             physical id: 0
             serial: 00CFD778
             slot: Bottom-Slot 1(top)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 1
             serial: Empty
             slot: Bottom-Slot 2(under)
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 8
          version: F.08
          date: 05/03/2012
          size: 128KiB
          capacity: 2496KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz
          vendor: Intel Corp.
          physical id: 18
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 1200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 1a
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 1b
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 1c
             slot: L3 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back unified
     *-cache
          description: L1 cache
          physical id: 19
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-pci
          description: Host bridge
          product: Ivy Bridge DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Ivy Bridge PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:c2000000-c2ffffff ioport:a0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Thames XT/GL [Radeon HD 7600M Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:47 memory:a0000000-afffffff memory:c2000000-c201ffff ioport:4000(size=256) memory:c2020000-c203ffff
        *-display
             description: VGA compatible controller
             product: Ivy Bridge Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:c3000000-c33fffff memory:b0000000-bfffffff ioport:5000(size=64)
        *-usb:0
             description: USB controller
             product: Panther Point USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:42 memory:c3600000-c360ffff
        *-communication
             description: Communication controller
             product: Panther Point MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:44 memory:c3614000-c361400f
        *-usb:1
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:c3619000-c36193ff
        *-multimedia
             description: Audio device
             product: Panther Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:c3610000-c3613fff
        *-pci:1
             description: PCI bridge
             product: Panther Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:c3500000-c35fffff
           *-network
                description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth1
                version: 01
                serial: e0:06:e6:18:6e:40
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.25.10 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:16 memory:c3500000-c3503fff
        *-pci:2
             description: PCI bridge
             product: Panther Point PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) ioport:c3400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 05
                serial: a0:b3:cc:79:41:23
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:3000(size=256) memory:c3404000-c3404fff memory:c3400000-c3403fff
        *-pci:3
             description: PCI bridge
             product: Panther Point PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) memory:c1000000-c1ffffff ioport:c0000000(size=16777216)
           *-generic UNCLAIMED
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:c1000000-c1000fff
        *-usb:2
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:c3618000-c36183ff
        *-isa
             description: ISA bridge
             product: Panther Point LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Panther Point 6 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi4
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:5088(size=8) ioport:5094(size=4) ioport:5080(size=8) ioport:5090(size=4) ioport:5060(size=32) memory:c3617000-c36177ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54755
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: JE3O
                serial: J2160051E9S75D
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=3c63052d
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: a66f-bb2b
                   size: 197MiB
                   capacity: 199MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2012-07-01 06:00:51 filesystem=ntfs label=SYSTEM state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /host
                   version: 3.1
                   serial: 8cf4223b-0e48-0f40-b127-4fe3cb6a5c97
                   size: 447GiB
                   capacity: 447GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-07-01 05:36:50 filesystem=ntfs label=HDD mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 9ffd10aa-dfba-44d0-bc3f-53b5fdbdff1b
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary swap initialized
                   configuration: filesystem=swap label=Linux_Swap pagesize=4096
              *-volume:3
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: FAT32
                   serial: 947d-62b1
                   size: 95MiB
                   capacity: 103MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ8B1
                vendor: hp
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: H.03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: Panther Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c3615000-c36150ff ioport:5040(size=32)
  *-battery
       description: Lithium Ion Battery
       product: MU06047
       vendor: Conexant (Rockwell)
       physical id: 1
       slot: Primary
       capacity: 47520mWh
       configuration: voltage=10.8V
```

Thanks.

EDIT1
TLP, Jupiter, laptop-mode-tools does not work.
Also my laptop is 1 yr old and i cleaned my ventilation.
Also it runs really cool on Windows 7 with the same performance.
Catalyst not working either.

---

### Post by abrake on 2013-08-11
One of the most common culprits for overheating laptops is poor ventilation. Do you use you laptop at a desk or with a stand? If you keep it on your lap, couch, bed, etc., the vents can easily be blocked and the cpu can overheat very quickly. 

Also, how old is this laptop? Over time dust can build up inside the chassis which can also prevent ventilation. If that's the case, you can go pick up a can of compressed air at a department store for about $5 and try to clean out the vents.

---

### Post by Mark Phelps on 2013-08-12
To reduce runtime temps, we used to recommend installing Jupiter -- but that has been abandoned.

Instead, you can try usinf tlp instead.

```
sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw

```
```

sudo tlp start
```

---

### Post by Yellow Pasque on 2013-08-12
It's an Intel/ATI hybrid graphics, so you may want to try installing Catalyst: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_13.4.2C_special_case_for_Intel.2BAC8-AMD_hybrid_graphics](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_13.4.2C_special_case_for_Intel.2BAC8-AMD_hybrid_graphics)

---

