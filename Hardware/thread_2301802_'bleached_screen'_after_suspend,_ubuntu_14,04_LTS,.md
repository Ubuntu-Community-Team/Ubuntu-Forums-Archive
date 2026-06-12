---
title: "'bleached screen' after suspend, ubuntu 14,04 LTS, intel core 2 duo 2009 imac."
date: 2015-11-05
forum: Hardware
---

### Post by pedrojulianfp on 2015-11-05
I recently installed Ubuntu 14.04 LTS on my 2009 Imac, just ubuntu without partitions,  everything works perfect, but after suspend, the screen shows some errors and comes back 'bleached', like white pixels all over the place.  After rebooting the problem is fixed.

Any help will be much appreciated .

---

### Post by mörgæs on 2015-11-05
Hi, welcome to the fora.

Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by gus11 on 2015-12-31
hi, i have the same issue as Pedrojulianftp on an 2007 iMac. Here is my hardware set up as you required, thx a lot for your help :

```
          fonctionnalités: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq        *-cache:0
             description: L2 cache
             identifiant matériel: 1
             emplacement: Unknown
             taille: 4MiB
             capacité: 4MiB
             fonctionnalités: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             identifiant matériel: 3
             emplacement: Unknown
             taille: 32KiB
             capacité: 32KiB
             fonctionnalités: asynchronous internal write-back data
     *-cache:0
          description: L1 cache
          identifiant matériel: 2
          emplacement: Unknown
          taille: 32KiB
          capacité: 32KiB
          fonctionnalités: asynchronous internal write-back instruction
     *-cpu:1
          description: CPU
          fabriquant: Intel(R) Corporation
          identifiant matériel: 4
          information bus: cpu@1
          version: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
          emplacement: U2E1
          taille: 2GHz
          capacité: 2GHz
          horloge: 200MHz
          fonctionnalités: cpufreq
        *-cache:0
             description: L2 cache
             identifiant matériel: 5
             emplacement: Unknown
             taille: 4MiB
             capacité: 4MiB
             fonctionnalités: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             identifiant matériel: 7
             emplacement: Unknown
             taille: 32KiB
             capacité: 32KiB
             fonctionnalités: asynchronous internal write-back data
     *-cache:1
          description: L1 cache
          identifiant matériel: 6
          emplacement: Unknown
          taille: 32KiB
          capacité: 32KiB
          fonctionnalités: asynchronous internal write-back instruction
     *-memory
          description: Mémoire Système
          identifiant matériel: 8
          emplacement: Carte mère
          taille: 3GiB
        *-bank:0
             description: SODIMM DDR2 Synchrone 667 MHz (1,5 ns)
             produit: M4 70T2953EZ3-CE6
             fabriquant: Samsung
             identifiant matériel: 0
             numéro de série: 0x241325A8
             emplacement: DIMM0
             taille: 1GiB
             bits: 64 bits
             horloge: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchrone 667 MHz (1,5 ns)
             produit: 0x4354324732533636374D2E4D313646480000
             fabriquant: 0x7F7F7F7F7F9B0000
             identifiant matériel: 1
             numéro de série: 0x00000000
             emplacement: DIMM1
             taille: 2GiB
             bits: 64 bits
             horloge: 667MHz (1.5ns)
     *-firmware
          description: BIOS
          fabriquant: Apple Inc.
          identifiant matériel: 11
          version: IM71.88Z.007A.B03.0803051705
          date: 03/05/08
          taille: 1MiB
          capacité: 1984KiB
          fonctionnalités: pci upgrade shadowing cdboot bootselect acpi ieee1394boot smartbattery netboot
     *-pci
          description: Host bridge
          produit: Mobile PM965/GM965/GL960 Memory Controller Hub
          fabriquant: Intel Corporation
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 03
          bits: 32 bits
          horloge: 33MHz
        *-pci:0
             description: PCI bridge
             produit: Mobile PM965/GM965/GL960 PCI Express Root Port
             fabriquant: Intel Corporation
             identifiant matériel: 1
             information bus: pci@0000:00:01.0
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:24 portE/S:3000(taille=4096) mémoire:d0600000-d06fffff portE/S:c0000000(taille=268435456)
           *-display
                description: VGA compatible controller
                produit: RV610/M74 [Mobility Radeon HD 2400 XT]
                fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
                identifiant matériel: 0
                information bus: pci@0000:01:00.0
                version: 00
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                ressources: irq:32 mémoire:c0000000-cfffffff mémoire:d0620000-d062ffff portE/S:3000(taille=256) mémoire:d0600000-d061ffff
        *-usb:0
             description: USB controller
             produit: 82801H (ICH8 Family) USB UHCI Controller #4
             fabriquant: Intel Corporation
             identifiant matériel: 1a
             information bus: pci@0000:00:1a.0
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             ressources: irq:20 portE/S:40c0(taille=32)
        *-usb:1
             description: USB controller
             produit: 82801H (ICH8 Family) USB UHCI Controller #5
             fabriquant: Intel Corporation
             identifiant matériel: 1a.1
             information bus: pci@0000:00:1a.1
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             ressources: irq:16 portE/S:40a0(taille=32)
        *-usb:2
             description: USB controller
             produit: 82801H (ICH8 Family) USB2 EHCI Controller #2
             fabriquant: Intel Corporation
             identifiant matériel: 1a.7
             information bus: pci@0000:00:1a.7
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             ressources: irq:21 mémoire:d0704c00-d0704fff
        *-multimedia
             description: Audio device
             produit: 82801H (ICH8 Family) HD Audio Controller
             fabriquant: Intel Corporation
             identifiant matériel: 1b
             information bus: pci@0000:00:1b.0
             version: 03
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             ressources: irq:31 mémoire:d0700000-d0703fff
        *-pci:1
             description: PCI bridge
             produit: 82801H (ICH8 Family) PCI Express Port 1
             fabriquant: Intel Corporation
             identifiant matériel: 1c
             information bus: pci@0000:00:1c.0
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:25 portE/S:5000(taille=4096) mémoire:d0500000-d05fffff portE/S:d0800000(taille=2097152)
        *-pci:2
             description: PCI bridge
             produit: 82801H (ICH8 Family) PCI Express Port 4
             fabriquant: Intel Corporation
             identifiant matériel: 1c.3
             information bus: pci@0000:00:1c.3
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:26 portE/S:6000(taille=4096) mémoire:d0400000-d04fffff portE/S:d0a00000(taille=2097152)
           *-firewire
                description: FireWire (IEEE 1394)
                produit: FW643 [TrueFire] PCIe 1394b Controller
                fabriquant: LSI Corporation
                identifiant matériel: 0
                information bus: pci@0000:03:00.0
                version: 05
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                ressources: irq:19 mémoire:d0400000-d0400fff
        *-pci:3
             description: PCI bridge
             produit: 82801H (ICH8 Family) PCI Express Port 5
             fabriquant: Intel Corporation
             identifiant matériel: 1c.4
             information bus: pci@0000:00:1c.4
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:27 portE/S:7000(taille=4096) mémoire:d0300000-d03fffff portE/S:d0000000(taille=1048576)
           *-network
                description: Interface réseau sans fil
                produit: BCM4321 802.11a/b/g/n
                fabriquant: Broadcom Corporation
                identifiant matériel: 0
                information bus: pci@0000:04:00.0
                nom logique: wlan0
                version: 03
                numéro de série: 00:1c:b3:73:29:de
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11abg
                ressources: irq:16 mémoire:d0300000-d0303fff mémoire:d0000000-d00fffff
        *-pci:4
             description: PCI bridge
             produit: 82801H (ICH8 Family) PCI Express Port 6
             fabriquant: Intel Corporation
             identifiant matériel: 1c.5
             information bus: pci@0000:00:1c.5
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:28 portE/S:2000(taille=4096) mémoire:d0200000-d02fffff portE/S:d0c00000(taille=2097152)
           *-network
                description: Ethernet interface
                produit: 88E8058 PCI-E Gigabit Ethernet Controller
                fabriquant: Marvell Technology Group Ltd.
                identifiant matériel: 0
                information bus: pci@0000:05:00.0
                nom logique: eth0
                version: 13
                numéro de série: 00:1b:63:9f:4d:d9
                capacité: 1Gbit/s
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
                ressources: irq:29 mémoire:d0200000-d0203fff portE/S:2000(taille=256) mémoire:d0220000-d023ffff
        *-usb:3
             description: USB controller
             produit: 82801H (ICH8 Family) USB UHCI Controller #1
             fabriquant: Intel Corporation
             identifiant matériel: 1d
             information bus: pci@0000:00:1d.0
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             ressources: irq:16 portE/S:4080(taille=32)
        *-usb:4
             description: USB controller
             produit: 82801H (ICH8 Family) USB UHCI Controller #2
             fabriquant: Intel Corporation
             identifiant matériel: 1d.1
             information bus: pci@0000:00:1d.1
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             ressources: irq:18 portE/S:4060(taille=32)
        *-usb:5
             description: USB controller
             produit: 82801H (ICH8 Family) USB UHCI Controller #3
             fabriquant: Intel Corporation
             identifiant matériel: 1d.2
             information bus: pci@0000:00:1d.2
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             ressources: irq:21 portE/S:4040(taille=32)
        *-usb:6
             description: USB controller
             produit: 82801H (ICH8 Family) USB2 EHCI Controller #1
             fabriquant: Intel Corporation
             identifiant matériel: 1d.7
             information bus: pci@0000:00:1d.7
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             ressources: irq:20 mémoire:d0704800-d0704bff
        *-pci:5
             description: PCI bridge
             produit: 82801 Mobile PCI Bridge
             fabriquant: Intel Corporation
             identifiant matériel: 1e
             information bus: pci@0000:00:1e.0
             version: f3
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci subtractive_decode bus_master cap_list
             ressources: mémoire:d0100000-d01fffff
        *-isa
             description: ISA bridge
             produit: 82801HM (ICH8M) LPC Interface Controller
             fabriquant: Intel Corporation
             identifiant matériel: 1f
             information bus: pci@0000:00:1f.0
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             ressources: irq:0
        *-ide
             description: IDE interface
             produit: 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
             fabriquant: Intel Corporation
             identifiant matériel: 1f.1
             information bus: pci@0000:00:1f.1
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: ide bus_master
             configuration: driver=ata_piix latency=0
             ressources: irq:21 portE/S:4108(taille=8) portE/S:411c(taille=4) portE/S:4100(taille=8) portE/S:4118(taille=4) portE/S:40e0(taille=16)
        *-storage
             description: SATA controller
             produit: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode]
             fabriquant: Intel Corporation
             identifiant matériel: 1f.2
             information bus: pci@0000:00:1f.2
             version: 03
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             ressources: irq:30 portE/S:40f8(taille=8) portE/S:4114(taille=4) portE/S:40f0(taille=8) portE/S:4110(taille=4) portE/S:4020(taille=32) mémoire:d0704000-d07047ff
        *-serial NON-RÉCLAMÉ
             description: SMBus
             produit: 82801H (ICH8 Family) SMBus Controller
             fabriquant: Intel Corporation
             identifiant matériel: 1f.3
             information bus: pci@0000:00:1f.3
             version: 03
             bits: 32 bits
             horloge: 33MHz
             configuration: latency=0
             ressources: mémoire:d0705000-d07050ff portE/S:efa0(taille=32)
     *-scsi:0
          identifiant matériel: 1
          nom logique: scsi0
          fonctionnalités: emulated
        *-cdrom
             description: DVD writer
             produit: DVD-R   UJ-85J
             fabriquant: MATSHITA
             identifiant matériel: 0.0.0
             information bus: scsi@0:0.0.0
             nom logique: /dev/cdrom
             nom logique: /dev/sr0
             version: FM0S
             fonctionnalités: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=open
     *-scsi:1
          identifiant matériel: 3
          nom logique: scsi2
          fonctionnalités: emulated
        *-disk
             description: ATA Disk
             produit: ST3250820AS Q
             fabriquant: Seagate
             identifiant matériel: 0.0.0
             information bus: scsi@2:0.0.0
             nom logique: /dev/sda
             version: E
             numéro de série: 5QE42DHR
             taille: 232GiB (250GB)
             fonctionnalités: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000057a8
           *-volume:0 NON-RÉCLAMÉ
                description: EFI GPT partition
                identifiant matériel: 1
                information bus: scsi@2:0.0.0,1
                capacité: 200MiB
                fonctionnalités: primary nofs
           *-volume:1
                description: Darwin/OS X HFS+ partition
                fabriquant: Mac OS X (journaled)
                identifiant matériel: 2
                information bus: scsi@2:0.0.0,2
                nom logique: /dev/sda2
                version: 4
                numéro de série: df439e74-141e-8347-0000-000000741000
                taille: 108GiB
                capacité: 108GiB
                fonctionnalités: primary bootable journaled osx hfsplus initialized
                configuration: boot=osx checked=2012-03-27 16:13:25 created=2012-03-27 07:13:25 filesystem=hfsplus lastmountedby=HFSJ modified=2015-12-30 21:50:15 state=clean
           *-volume:2
                description: Linux swap volume
                identifiant matériel: 3
                information bus: scsi@2:0.0.0,3
                nom logique: /dev/sda3
                version: 1
                numéro de série: fd495ed2-75d7-400c-9662-dc20f5e4a224
                taille: 7879MiB
                capacité: 7879MiB
                fonctionnalités: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:3
                description: Darwin/OS X HFS+ partition
                fabriquant: Mac OS X (journaled)
                identifiant matériel: 4
                information bus: scsi@2:0.0.0,4
                nom logique: /dev/sda4
                version: 4
                numéro de série: b7bda144-3798-6e07-0000-000000005000
                taille: 619MiB
                capacité: 619MiB
                fonctionnalités: primary journaled bootable macos osx hfsplus initialized
                configuration: boot=osx checked=2012-11-28 13:54:30 created=2012-11-28 04:54:30 filesystem=hfsplus lastmountedby=HFSJ modified=2015-12-30 21:50:07 state=clean
     *-scsi:2
          identifiant matériel: 5
          information bus: usb@1:2
          nom logique: scsi6
          fonctionnalités: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             identifiant matériel: 0.0.0
             information bus: scsi@6:0.0.0
             nom logique: /dev/sdb
             taille: 232GiB (250GB)
             fonctionnalités: gpt-1.00 partitioned partitioned:gpt
             configuration: guid=093c6709-96f3-4764-b601-61de54af1a8b sectorsize=512
           *-volume:0
                description: Windows FAT volume
                fabriquant: BSD  4.4
                identifiant matériel: 1
                information bus: scsi@6:0.0.0,1
                nom logique: /dev/sdb1
                version: FAT32
                numéro de série: 67e3-17ed
                taille: 199MiB
                capacité: 199MiB
                fonctionnalités: boot fat initialized
                configuration: FATs=2 filesystem=fat label=EFI name=EFI System Partition
           *-volume:1
                description: Apple HFS+ partition
                fabriquant: Mac OS X (journaled)
                identifiant matériel: 2
                information bus: scsi@6:0.0.0,2
                nom logique: /dev/sdb2
                nom logique: /media/guest-qBf5uJ/Ext
                version: 4
                numéro de série: 9bbe16e2-567c-c25d-0000-000000745000
                taille: 232GiB
                fonctionnalités: journaled hfsplus initialized
                configuration: checked=2015-12-07 12:45:24 created=2015-12-07 12:45:24 filesystem=hfsplus lastmountedby=HFSJ modified=2015-12-30 21:50:08 mount.fstype=hfsplus mount.options=ro,nosuid,nodev,relatime,umask=22,uid=0,gid=0,nls=utf8 name=Ext state=mounted



```

---

### Post by mörgæs on 2016-01-03
Sorry, I don't know this graphics card well enough to give advice.

---

