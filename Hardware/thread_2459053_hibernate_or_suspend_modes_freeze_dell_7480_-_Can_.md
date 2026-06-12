---
title: "hibernate or suspend modes freeze dell 7480 - Can Ubuntu use s2ram?"
date: 2021-03-09
forum: Hardware
---

### Post by Thibaud74 on 2021-03-09
Hi,

How can I do my system use s2ram and not pm-suspend? It seems that Ubuntu uses the second method...?

As soon as the computer hibernates or goes on suspend mode, a black screen apairs and it never comes back unless I switch off the laptop.
This behavior is very distrubing because the computer launches the suspend time just 1 minute after I unplug it.


My hardware :
```
thibaud-latitude-7480
    description: Ordinateur Bloc-notes
    produit: Latitude 7480 (07A0)
    fabricant: Dell Inc.
    numéro de série: 7DCVLH2
    bits: 64 bits
    fonctionnalités: smbios-3.0.0 dmi-3.0.0 smp vsyscall32
    configuration : boot=normal chassis=notebook family=Latitude sku=07A0 uuid=44454C4C-4400-1043-8056-B7C04F4C4832
  *-core
       description: Carte mère
       produit: 00F6D3
       fabricant: Dell Inc.
       identifiant matériel: 0
       version: A00
       numéro de série: /7DCVLH2/CN129637AI157A/
     *-firmware
          description: BIOS
          fabricant: Dell Inc.
          identifiant matériel: 0
          version: 1.19.0
          date: 07/26/2020
          taille: 64KiB
          capacité: 16MiB
          fonctionnalités: pci pnp upgrade shadowing cdboot bootselect edd int13floppynec int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-memory
          description: Mémoire Système
          identifiant matériel: 45
          emplacement: Carte mère
          taille: 16GiB
        *-bank:0
             description: SODIMM DDR4 Synchrone Unbuffered (Unregistered) 2400 MHz (0,4 ns)
             produit: K821PJ-MIH
             fabricant: AMD
             identifiant matériel: 0
             numéro de série: E1124695
             emplacement: DIMM A
             taille: 16GiB
             bits: 64 bits
             horloge: 2400MHz (0.4ns)
        *-bank:1
             description: DIMMProject-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2021-01-19 19:00+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2021-01-21 18:43+0000X-Generator: Launchpad (build 2d1d5e352f0d063d660df2300e31f66bed027fa5) [vide]
             identifiant matériel: 1
             emplacement: ChannelB-DIMM0
     *-cache:0
          description: L1 cache
          identifiant matériel: 49
          emplacement: L1 Cache
          taille: 128KiB
          capacité: 128KiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=1
     *-cache:1
          description: L2 cache
          identifiant matériel: 4a
          emplacement: L2 Cache
          taille: 512KiB
          capacité: 512KiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=2
     *-cache:2
          description: L3 cache
          identifiant matériel: 4b
          emplacement: L3 Cache
          taille: 3MiB
          capacité: 3MiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=3
     *-cpu
          description: CPU
          produit: Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
          fabricant: Intel Corp.
          identifiant matériel: 4c
          information bus: cpu@0
          version: Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
          numéro de série: To Be Filled By O.E.M.
          emplacement: U3E1
          taille: 2913MHz
          capacité: 3100MHz
          bits: 64 bits
          horloge: 100MHz
          fonctionnalités: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
          configuration : cores=2 enabledcores=2 threads=4
     *-generic:0 NON-RÉCLAMÉ
          identifiant matériel: 2020
          information bus: parisc@2020
     *-generic:1 NON-RÉCLAMÉ
          identifiant matériel: 2021
          information bus: parisc@2021
     *-pci
          description: Host bridge
          produit: Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
          fabricant: Intel Corporation
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 02
          bits: 32 bits
          horloge: 33MHz
          configuration : driver=skl_uncore
          ressources : irq:0
        *-display
             description: VGA compatible controller
             produit: HD Graphics 620
             fabricant: Intel Corporation
             identifiant matériel: 2
             information bus: pci@0000:00:02.0
             version: 02
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration : driver=i915 latency=0
             ressources : irq:129 mémoire:eb000000-ebffffff mémoire:a0000000-afffffff portE/S:f000(taille=64) mémoire:c0000-dffff
        *-generic:0
             description: Signal processing controller
             produit: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
             fabricant: Intel Corporation
             identifiant matériel: 4
             information bus: pci@0000:00:04.0
             version: 02
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: msi pm cap_list
             configuration : driver=proc_thermal latency=0
             ressources : irq:16 mémoire:ec240000-ec247fff
        *-usb
             description: USB controller
             produit: Sunrise Point-LP USB 3.0 xHCI Controller
             fabricant: Intel Corporation
             identifiant matériel: 14
             information bus: pci@0000:00:14.0
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi xhci bus_master cap_list
             configuration : driver=xhci_hcd latency=0
             ressources : irq:125 mémoire:ec230000-ec23ffff
           *-usbhost:0
                produit: xHCI Host Controller
                fabricant: Linux 5.4.0-66-lowlatency xhci-hcd
                identifiant matériel: 0
                information bus: usb@1
                nom logique: usb1
                version: 5.04
                fonctionnalités: usb-2.00
                configuration : driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Vidéo
                   produit: Integrated_Webcam_HD
                   fabricant: CNFGH19N3551120030C2
                   identifiant matériel: 5
                   information bus: usb@1:5
                   version: 68.25
                   fonctionnalités: usb-2.00
                   configuration : driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: Interface sans fil Bluetooth
                   fabricant: Intel Corp.
                   identifiant matériel: 7
                   information bus: usb@1:7
                   version: 0.10
                   fonctionnalités: bluetooth usb-2.00
                   configuration : driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                produit: xHCI Host Controller
                fabricant: Linux 5.4.0-66-lowlatency xhci-hcd
                identifiant matériel: 1
                information bus: usb@2
                nom logique: usb2
                version: 5.04
                fonctionnalités: usb-3.00
                configuration : driver=hub slots=6 speed=5000Mbit/s
        *-generic:1
             description: Signal processing controller
             produit: Sunrise Point-LP Thermal subsystem
             fabricant: Intel Corporation
             identifiant matériel: 14.2
             information bus: pci@0000:00:14.2
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi cap_list
             configuration : driver=intel_pch_thermal latency=0
             ressources : irq:18 mémoire:ec259000-ec259fff
        *-generic:2
             description: Signal processing controller
             produit: Sunrise Point-LP Serial IO I2C Controller #0
             fabricant: Intel Corporation
             identifiant matériel: 15
             information bus: pci@0000:00:15.0
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration : driver=intel-lpss latency=0
             ressources : irq:16 mémoire:ec258000-ec258fff
        *-generic:3
             description: Signal processing controller
             produit: Sunrise Point-LP Serial IO I2C Controller #1
             fabricant: Intel Corporation
             identifiant matériel: 15.1
             information bus: pci@0000:00:15.1
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration : driver=intel-lpss latency=0
             ressources : irq:17 mémoire:ec257000-ec257fff
        *-generic:4
             description: Signal processing controller
             produit: Sunrise Point-LP Serial IO I2C Controller #2
             fabricant: Intel Corporation
             identifiant matériel: 15.2
             information bus: pci@0000:00:15.2
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration : driver=intel-lpss latency=0
             ressources : irq:18 mémoire:ec256000-ec256fff
        *-communication
             description: Communication controller
             produit: Sunrise Point-LP CSME HECI #1
             fabricant: Intel Corporation
             identifiant matériel: 16
             information bus: pci@0000:00:16.0
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration : driver=mei_me latency=0
             ressources : irq:130 mémoire:ec255000-ec255fff
        *-raid
             description: RAID bus controller
             produit: 82801 Mobile SATA Controller [RAID mode]
             fabricant: Intel Corporation
             identifiant matériel: 17
             information bus: pci@0000:00:17.0
             version: 21
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: raid msi pm bus_master cap_list
             configuration : driver=ahci latency=0
             ressources : irq:127 mémoire:ec250000-ec251fff mémoire:ec254000-ec2540ff portE/S:f090(taille=8) portE/S:f080(taille=4) portE/S:f060(taille=32) mémoire:ec253000-ec2537ff
        *-pci:0
             description: PCI bridge
             produit: Sunrise Point-LP PCI Express Root Port #1
             fabricant: Intel Corporation
             identifiant matériel: 1c
             information bus: pci@0000:00:1c.0
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:122 mémoire:ec100000-ec1fffff
           *-generic
                description: Unassigned class
                produit: RTS525A PCI Express Card Reader
                fabricant: Realtek Semiconductor Co., Ltd.
                identifiant matériel: 0
                information bus: pci@0000:01:00.0
                version: 01
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list
                configuration : driver=rtsx_pci latency=0
                ressources : irq:126 mémoire:ec100000-ec100fff
        *-pci:1
             description: PCI bridge
             produit: Sunrise Point-LP PCI Express Root Port #3
             fabricant: Intel Corporation
             identifiant matériel: 1c.2
             information bus: pci@0000:00:1c.2
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:123 mémoire:ec000000-ec0fffff
           *-network
                description: Interface réseau sans fil
                produit: Wireless 8265 / 8275
                fabricant: Intel Corporation
                identifiant matériel: 0
                information bus: pci@0000:02:00.0
                nom logique: wlp2s0
                version: 78
                numéro de série: f8:94:c2:50:82:c8
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration : broadcast=yes driver=iwlwifi driverversion=5.4.0-66-lowlatency firmware=36.77d01142.0 ip=192.168.0.39 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                ressources : irq:131 mémoire:ec000000-ec001fff
        *-pci:2
             description: PCI bridge
             produit: Sunrise Point-LP PCI Express Root Port #5
             fabricant: Intel Corporation
             identifiant matériel: 1c.4
             information bus: pci@0000:00:1c.4
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:124 portE/S:2000(taille=4096) mémoire:d4000000-ea0fffff portE/S:b0000000(taille=570425344)
        *-isa
             description: ISA bridge
             produit: Sunrise Point LPC Controller/eSPI Controller
             fabricant: Intel Corporation
             identifiant matériel: 1f
             information bus: pci@0000:00:1f.0
             version: 21
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: isa
             configuration : latency=0
        *-memory NON-RÉCLAMÉ
             description: Memory controller
             produit: Sunrise Point-LP PMC
             fabricant: Intel Corporation
             identifiant matériel: 1f.2
             information bus: pci@0000:00:1f.2
             version: 21
             bits: 32 bits
             horloge: 33MHz (30.3ns)
             configuration : latency=0
             ressources : mémoire:ec24c000-ec24ffff
        *-multimedia
             description: Audio device
             produit: Sunrise Point-LP HD Audio
             fabricant: Intel Corporation
             identifiant matériel: 1f.3
             information bus: pci@0000:00:1f.3
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration : driver=snd_hda_intel latency=32
             ressources : irq:132 mémoire:ec248000-ec24bfff mémoire:ec220000-ec22ffff
        *-serial
             description: SMBus
             produit: Sunrise Point-LP SMBus
             fabricant: Intel Corporation
             identifiant matériel: 1f.4
             information bus: pci@0000:00:1f.4
             version: 21
             bits: 64 bits
             horloge: 33MHz
             configuration : driver=i801_smbus latency=0
             ressources : irq:16 mémoire:ec252000-ec2520ff portE/S:f040(taille=32)
        *-network
             description: Ethernet interface
             produit: Ethernet Connection (4) I219-LM
             fabricant: Intel Corporation
             identifiant matériel: 1f.6
             information bus: pci@0000:00:1f.6
             nom logique: enp0s31f6
             version: 21
             numéro de série: a4:4c:c8:53:3a:ca
             capacité: 1Gbit/s
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration : autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
             ressources : irq:128 mémoire:ec200000-ec21ffff
     *-pnp00:00
          produit: PnP device PNP0c02
          identifiant matériel: 1
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:01
          produit: PnP device PNP0b00
          identifiant matériel: 2
          fonctionnalités: pnp
          configuration : driver=rtc_cmos
     *-pnp00:02
          produit: PnP device INT3f0d
          fabricant: Interphase Corporation
          identifiant matériel: 3
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:03
          produit: PnP device PNP0303
          identifiant matériel: 4
          fonctionnalités: pnp
          configuration : driver=i8042 kbd
     *-pnp00:04
          produit: PnP device PNP0c02
          identifiant matériel: 5
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:05
          produit: PnP device PNP0c02
          identifiant matériel: 6
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:06
          produit: PnP device PNP0c02
          identifiant matériel: 7
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:07
          produit: PnP device PNP0c02
          identifiant matériel: 8
          fonctionnalités: pnp
          configuration : driver=system
     *-scsi
          identifiant matériel: 9
          nom logique: scsi2
          fonctionnalités: emulated
        *-disk
             description: ATA Disk
             produit: INTEL SSDSCKKF51
             identifiant matériel: 0.0.0
             information bus: scsi@2:0.0.0
             nom logique: /dev/sda
             version: D11N
             numéro de série: CVLY709102XS512K
             taille: 476GiB (512GB)
             fonctionnalités: gpt-1.00 partitioned partitioned:gpt
             configuration : ansiversion=5 guid=9ea7625a-82a5-4cab-83e1-0379249ac9f5 logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                fabricant: MSDOS5.0
                identifiant matériel: 1
                information bus: scsi@2:0.0.0,1
                nom logique: /dev/sda1
                nom logique: /boot/efi
                version: FAT32
                numéro de série: f2e1-ff96
                taille: 596MiB
                capacité: 599MiB
                fonctionnalités: boot fat initialized
                configuration : FATs=2 filesystem=fat label=ESP mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:1
                description: Windows FAT volume
                fabricant: MSDOS5.0
                identifiant matériel: 2
                information bus: scsi@2:0.0.0,2
                nom logique: /dev/sda2
                version: FAT32
                numéro de série: 70fb-538f
                taille: 3044MiB
                capacité: 3071MiB
                fonctionnalités: fat initialized
                configuration : FATs=2 filesystem=fat label=OS name=Basic data partition
           *-volume:2
                description: Volume EXT4
                fabricant: Linux
                identifiant matériel: 3
                information bus: scsi@2:0.0.0,3
                nom logique: /dev/sda3
                nom logique: /
                version: 1.0
                numéro de série: 724e3939-7a6c-41d1-828a-c747817c1a33
                taille: 420GiB
                fonctionnalités: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration : created=2017-10-18 14:12:35 filesystem=ext4 label=UBUNTU lastmountpoint=/ modified=2021-03-09 10:56:07 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2021-03-09 10:56:08 state=mounted
           *-volume:3
                description: Linux swap volume
                fabricant: Linux
                identifiant matériel: 4
                information bus: scsi@2:0.0.0,4
                nom logique: /dev/sda4
                version: 1
                numéro de série: 71efb358-0b35-4fdb-8340-0f430c54f839
                taille: 31GiB
                capacité: 31GiB
                fonctionnalités: nofs swap initialized
                configuration : filesystem=swap pagesize=4095
           *-volume:4
                description: Volume EXT4
                fabricant: Linux
                identifiant matériel: 5
                information bus: scsi@2:0.0.0,5
                nom logique: /dev/sda5
                version: 1.0
                numéro de série: e2e7af2e-7075-4a07-9735-8d96d01f466d
                taille: 191MiB
                fonctionnalités: journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration : created=2020-12-23 07:41:44 filesystem=ext4 modified=2021-02-26 10:41:15 mounted=2021-02-26 10:41:15 state=clean
           *-volume:5
                description: Volume EXT4
                fabricant: Linux
                identifiant matériel: 6
                information bus: scsi@2:0.0.0,6
                nom logique: /dev/sda6
                version: 1.0
                numéro de série: 4794760f-67c7-4394-87b6-7178b8c9ae1a
                taille: 21GiB
                fonctionnalités: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration : created=2020-12-23 09:58:11 filesystem=ext4 lastmountpoint=/media/sda6 modified=2021-02-26 17:43:46 mounted=2021-02-26 13:00:19 state=clean
  *-battery
       produit: DELL PGFX484
       fabricant: SMP
       identifiant matériel: 1
       version: 07/25/2019
       numéro de série: 0464
       emplacement: Sys. Battery Bay
       capacité: 41990mWh
       configuration : voltage=11,4V
```

After a "sudo systemctl hibernate", dmesg get this error messages in red:
```

dmesg -l err
[    2.992633] systemd[1]: dm-event.socket: Socket service dm-event.service not loaded, refusing.
[    2.992637] systemd[1]: Failed to listen on Device-mapper event daemon FIFOs.
[    2.992697] systemd[1]: lvm2-lvmpolld.socket: Socket service lvm2-lvmpolld.service not loaded, refusing.
[    2.992701] systemd[1]: Failed to listen on LVM2 poll daemon socket.
[   78.011357] iwlwifi 0000:02:00.0: iwl_trans_send_cmd bad state = 0
[   78.516020] i2c_hid i2c-DLL07A0:01: i2c_hid_get_input: incomplete report (83/65369)
[   90.707761] ACPI BIOS Error (bug): Failure creating named object [\_GPE.XTBT.SPRT], AE_ALREADY_EXISTS (20190816/dswload2-326)
[   90.707782] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
[   90.707786] ACPI Error: Aborting method \_GPE.XTBT due to previous error (AE_ALREADY_EXISTS) (20190816/psparse-529)
[   90.707791] ACPI Error: Aborting method \_GPE.XTBT due to previous error (AE_ALREADY_EXISTS) (20190816/psparse-529)
[   90.707798] ACPI Error: Aborting method \_GPE._E42 due to previous error (AE_ALREADY_EXISTS) (20190816/psparse-529)
[   90.707807] ACPI Error: AE_ALREADY_EXISTS, while evaluating GPE method [_E42] (20190816/evgpe-511)
[  136.649785] xhci_hcd 0000:3b:00.0: PCI post-resume error -19!
[  136.649796] xhci_hcd 0000:3b:00.0: HC died; cleaning up

```

Best,
Thibaud.

---

