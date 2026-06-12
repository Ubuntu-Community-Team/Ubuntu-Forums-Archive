---
title: "Random freezing + lost wifi (hardware vs. kernel pb?)"
date: 2016-01-28
forum: Hardware
---

### Post by Stazzy on 2016-01-28
I have had a pretty annoying problem with Linux distros lately. 
I have a Asus Eee Pc 1215b (netbook) and I've been using it without problems 'till maybe the last week or so. 
I had a Linux Mint 13 mate, so I tought maybe the problem will be solved by an upgrade -> 17.3 xfce. Well, no. 
So I installed (fresh install) Lubuntu 14.04... to no avail. The problem restarts. 

Basically the computer freezes completely. No mouse, no keyboard, ctrl+alt+backspace (or del) don't work. The only way is to reboot computer from the power button...  And when I do that, I lose the wireless card. I suppose the network manager crashes and it doesn't find wireless card anymore at all. Like it didn't exist. I need to reinstall network-manager, or restart it, reboot... and hope it works. Sometimes it does, sometimes not. 
And then the computer freezes again. The pb reminds a lot of: [http://bugs.launchpad.net/linuxmint/+bug/1321623](http://bugs.launchpad.net/linuxmint/+bug/1321623)

I cannot reproduce the freezing. It seems to me, it may have something to do with Firefox / flash, but not only. Same thing has happened without browser running. 

As my computer worked fine 'till last week or so, I've started to ask myself if I have compatibility issues with the latest Kernels. But well, then I'm just no expert enough for knowing how to find an answer and, if that's the case, how to go back to an older kernel... (I'm pretty happy with Lubuntu, just that sound doesn't work yet, but thats an another pb)

lshw :

```
description: Ordinateur Bloc-notes
    produit: 1215B (1215B)
    fabriquant: ASUSTeK Computer INC.
    version: x.x
    numéro de série: BAOAAS233427
    bits: 64 bits
    fonctionnalités: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=notebook family=Eee PC sku=1215B uuid=00640ECF-EF61-4881-2040-5404A624DE47
  *-core
       description: Carte mère
       produit: 1215B
       fabriquant: ASUSTeK Computer INC.
       identifiant matériel: 0
       version: x.xx
       numéro de série: EeePC-0123456789
       emplacement: To be filled by O.E.M.
     *-firmware:0
          description: BIOS
          fabriquant: American Megatrends Inc.
          identifiant matériel: 0
          version: 0401
          date: 06/17/2011
          taille: 64KiB
          capacité: 1984KiB
          fonctionnalités: pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          produit: AMD C-60 APU with Radeon(tm) HD Graphics
          fabriquant: Advanced Micro Devices [AMD]
          identifiant matériel: 1
          information bus: cpu@0
          version: AMD C-60 APU with Radeon(tm) HD Graphics
          numéro de série: To Be Filled By O.E.M.
          emplacement: CPU 1
          taille: 1GHz
          capacité: 1333MHz
bits: 64 bits
          horloge: 100MHz
          fonctionnalités: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter vmmcall cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             identifiant matériel: 0
             emplacement: L1-Cache
             taille: 128KiB
             capacité: 128KiB
             fonctionnalités: internal write-back unified
        *-cache:1
             description: L2 cache
             identifiant matériel: 1
             emplacement: L2-Cache
             taille: 1MiB
             capacité: 1MiB
             fonctionnalités: internal varies data
        *-cache:2
             description: L1 cache
             identifiant matériel: 2
             emplacement: L1-Cache
             taille: 128KiB
             capacité: 128KiB
             fonctionnalités: internal write-back unified
        *-cache:3
             description: L2 cache
             identifiant matériel: 3
             emplacement: L2-Cache
             taille: 1MiB
             capacité: 1MiB
             fonctionnalités: internal varies data
     *-memory:0
          description: Mémoire Système
          identifiant matériel: 2
          emplacement: Carte mère
        *-bank:0
             description: DIMM DDR3 Synchrone 1333 MHz (0,8 ns)
             produit: M471B5773DH0-CH9
             fabriquant: Samsung
             identifiant matériel: 0
             numéro de série: B15589B3
             emplacement: A1_DIMM0
             taille: 2GiB
             bits: 64 bits
             horloge: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchrone 1333 MHz (0,8 ns)
             produit: M471B5773DH0-CH9
             fabriquant: Samsung
             identifiant matériel: 1
             numéro de série: B15589A1
             emplacement: A1_DIMM1
             taille: 2GiB
             bits: 64 bits
             horloge: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR3 Synchrone 1333 MHz (0,8 ns)
             produit: M471B5773DH0-CH9
             fabriquant: Samsung
             identifiant matériel: 2
             numéro de série: B15589B3
             emplacement: A1_DIMM0
             taille: 2GiB
             bits: 64 bits
             horloge: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 Synchrone 1333 MHz (0,8 ns)
             produit: M471B5773DH0-CH9
             fabriquant: Samsung
             identifiant matériel: 3
             numéro de série: B15589A1
             emplacement: A1_DIMM1
             taille: 2GiB
             bits: 64 bits
             horloge: 1333MHz (0.8ns)
     *-firmware:1
          description: BIOS
          fabriquant: American Megatrends Inc.
          identifiant matériel: 3
          version: 0401
          date: 06/17/2011
          taille: 64KiB
          capacité: 1984KiB
          fonctionnalités: pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:1
          description: CPU
          produit: (To Be Filled By O.E.M.)
          fabriquant: AMD C-60 APU with
          identifiant matériel: 4
          information bus: cpu@1
          version: AMD C-60 APU with Radeon(tm) HD Graphics
          numéro de série: To Be Filled By O.E.M.
          emplacement: CPU 1
          taille: 800MHz
          capacité: 1333MHz
          horloge: 100MHz
          fonctionnalités: x86-64 cpufreq
          configuration: cores=2 enabledcores=2
     *-memory:1
          description: Mémoire Système
          identifiant matériel: 5
          emplacement: Carte mère
     *-memory:2 NON-RÉCLAMÉ
          identifiant matériel: 6
     *-memory:3 NON-RÉCLAMÉ
          identifiant matériel: 7
     *-pci:0
          description: Host bridge
          produit: Family 14h Processor Root Complex
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 00
          bits: 32 bits
          horloge: 66MHz
          configuration: latency=32
        *-display
             description: VGA compatible controller
             produit: Wrestler [Radeon HD 6290]
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 1
             information bus: pci@0000:00:01.0
             version: 00
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             ressources: irq:25 mémoire:c0000000-cfffffff portE/S:f000(taille=256) mémoire:feb00000-feb3ffff
        *-multimedia:0
             description: Audio device
             produit: Wrestler HDMI Audio
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 1.1
             information bus: pci@0000:00:01.1
             version: 00
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             ressources: irq:24 mémoire:feb44000-feb47fff
        *-pci:0
             description: PCI bridge
             produit: Family 14h Processor Root Port
             fabriquant: Advanced Micro Devices, Inc. [AMD]
             identifiant matériel: 4
             information bus: pci@0000:00:04.0
             version: 00
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:16 mémoire:fea00000-feafffff
           *-network
                description: Interface réseau sans fil
                produit: AR9285 Wireless Network Adapter (PCI-Express)
                fabriquant: Qualcomm Atheros
                identifiant matériel: 0
                information bus: pci@0000:01:00.0
                nom logique: wlan0
                version: 01
                numéro de série: 74:2f:68:4d:f8:4e
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.19.0-47-generic firmware=N/A ip=192.168.0.26 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                ressources: irq:16 mémoire:fea00000-fea0ffff
        *-pci:1
             description: PCI bridge
             produit: Family 14h Processor Root Port
             fabriquant: Advanced Micro Devices, Inc. [AMD]
             identifiant matériel: 5
             information bus: pci@0000:00:05.0
             version: 00
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:17 portE/S:e000(taille=4096) mémoire:fe900000-fe9fffff
           *-network
                description: Ethernet interface
                produit: AR8152 v2.0 Fast Ethernet
                fabriquant: Qualcomm Atheros
                identifiant matériel: 0
                information bus: pci@0000:02:00.0
                nom logique: eth0
                version: c1
                numéro de série: 54:04:a6:24:de:47
                taille: 100Mbit/s
                capacité: 100Mbit/s
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.0.40 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                ressources: irq:26 mémoire:fe900000-fe93ffff portE/S:e000(taille=128)
        *-storage
             description: SATA controller
             produit: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 11
             information bus: pci@0000:00:11.0
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             ressources: irq:19 portE/S:f140(taille=8) portE/S:f130(taille=4) portE/S:f120(taille=8) portE/S:f110(taille=4) portE/S:f100(taille=16) mémoire:feb4c000-feb4c3ff
        *-usb:0
             description: USB controller
             produit: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 12
             information bus: pci@0000:00:12.0
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: ohci bus_master
             configuration: driver=ohci-pci latency=32
             ressources: irq:18 mémoire:feb4b000-feb4bfff
        *-usb:1
             description: USB controller
             produit: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 12.2
             information bus: pci@0000:00:12.2
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             ressources: irq:17 mémoire:feb4a000-feb4a0ff
        *-usb:2
             description: USB controller
             produit: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 13
             information bus: pci@0000:00:13.0
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: ohci bus_master
             configuration: driver=ohci-pci latency=32
             ressources: irq:18 mémoire:feb49000-feb49fff
        *-usb:3
             description: USB controller
             produit: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 13.2
             information bus: pci@0000:00:13.2
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             ressources: irq:17 mémoire:feb48000-feb480ff
        *-serial NON-RÉCLAMÉ
             description: SMBus
             produit: SBx00 SMBus Controller
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 14
             information bus: pci@0000:00:14.0
             version: 42
             bits: 32 bits
             horloge: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             produit: SBx00 Azalia (Intel HDA)
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 14.2
             information bus: pci@0000:00:14.2
             version: 40
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             ressources: irq:16 mémoire:feb40000-feb43fff
        *-isa
             description: ISA bridge
             produit: SB7x0/SB8x0/SB9x0 LPC host controller
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 14.3
             information bus: pci@0000:00:14.3
             version: 40
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             produit: SBx00 PCI to PCI Bridge
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 14.4
             information bus: pci@0000:00:14.4
             version: 40
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: pci subtractive_decode bus_master vga_palette
        *-pci:3
             description: PCI bridge
             produit: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 15
             information bus: pci@0000:00:15.0
             version: 00
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:16 portE/S:d000(taille=4096) mémoire:fdf00000-fe8fffff portE/S:d0000000(taille=268435456)
     *-pci:1
          description: Host bridge
          produit: Family 12h/14h Processor Function 0
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 101
          information bus: pci@0000:00:18.0
          version: 43
          bits: 32 bits
          horloge: 33MHz
     *-pci:2
          description: Host bridge
          produit: Family 12h/14h Processor Function 1
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 102
          information bus: pci@0000:00:18.1
          version: 00
          bits: 32 bits
          horloge: 33MHz
     *-pci:3
          description: Host bridge
          produit: Family 12h/14h Processor Function 2
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 103
          information bus: pci@0000:00:18.2
          version: 00
          bits: 32 bits
          horloge: 33MHz
     *-pci:4
          description: Host bridge
          produit: Family 12h/14h Processor Function 3
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 104
          information bus: pci@0000:00:18.3
          version: 00
          bits: 32 bits
          horloge: 33MHz
          configuration: driver=k10temp
          ressources: irq:0
     *-pci:5
          description: Host bridge
          produit: Family 12h/14h Processor Function 4
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 105
          information bus: pci@0000:00:18.4
          version: 00
          bits: 32 bits
          horloge: 33MHz
     *-pci:6
          description: Host bridge
          produit: Family 12h/14h Processor Function 6
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 106
          information bus: pci@0000:00:18.5
          version: 00
          bits: 32 bits
          horloge: 33MHz
     *-pci:7
          description: Host bridge
          produit: Family 12h/14h Processor Function 5
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 107
          information bus: pci@0000:00:18.6
          version: 00
          bits: 32 bits
          horloge: 33MHz
     *-pci:8
          description: Host bridge
          produit: Family 12h/14h Processor Function 7
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 108
          information bus: pci@0000:00:18.7
          version: 00
          bits: 32 bits
          horloge: 33MHz
     *-scsi
          identifiant matériel: 8
          nom logique: scsi0
          fonctionnalités: emulated
        *-disk
             description: ATA Disk
             produit: ST9320325AS
             fabriquant: Seagate
             identifiant matériel: 0.0.0
             information bus: scsi@0:0.0.0
             nom logique: /dev/sda
             version: SDM1
             numéro de série: 6VDD3PXK
             taille: 298GiB (320GB)
             fonctionnalités: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00087c13
           *-volume:0
                description: Linux filesystem partition
                fabriquant: Linux
                identifiant matériel: 1
                information bus: scsi@0:0.0.0,1
                nom logique: /dev/sda1
                nom logique: /boot
                version: 1.0
                numéro de série: cbab55b5-94d4-4436-9f1d-705e1468973a
                taille: 243MiB
                capacité: 243MiB
                fonctionnalités: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2016-01-28 21:12:13 mount.fstype=ext2 mount.options=rw,relatime mounted=2016-01-28 21:12:13 state=mounted
           *-volume:1
                description: Extended partition
                identifiant matériel: 2
                information bus: scsi@0:0.0.0,2
                nom logique: /dev/sda2
                taille: 297GiB
                capacité: 297GiB
                fonctionnalités: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   identifiant matériel: 5
                   nom logique: /dev/sda5
                   numéro de série: TZUAG0-KNLS-WnxY-IeuY-YALa-yIEj-Shnr2H
                   taille: 297GiB
                   capacité: 297GiB
                   fonctionnalités: multi lvm2


```

I would be happy with any good guesses... thanks!


Edit://
Now that I'm thinking of it, maybe the wireless card causes something? I don't remind having any problems when the computer is connected with Ethernet cable, like right now.

---

### Post by weatherman2 on 2016-01-28
Go back to the last old distro (boot it live from USB) that worked.  See if you still have the freezing problem.  If you do, I suspect a hardware problem - one of two good possiblities:

1. Bad RAM.  Run Memtest for a good hour or more and see if you get any errors.  (Every Ubuntu boot USB includes Memtest in the menu - hit the Esc key as soon as the USB starts to boot to get a menu - after you choose the language.)  Yes, RAM does occasionally go bad.

2. Dirty CPU fan/heat sink and overheating.  This is very common on older laptops.  Often this will cause random shutdowns but could also cause freezing.  You'd be more likely to see this after the laptop has been on for a while vs. when it is cold.

---

### Post by promet on 2016-01-28
I am having this precise problem as well. Also, just started very recently (within the last two weeks or so I would say).

Output of lshw:

```

shivuxnext
    description: Computer
    width: 64 bits
    capabilities: smbios-2.7 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 15GiB
     *-cpu
          product: AMD FX(tm)-8320 Eight-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 1400MHz
          capacity: 3500MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht  syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good  nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma  cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm  extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop  skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb  arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean  flushbyasid decodeassists pausefilter pfthreshold vmmcall bmi1 cpufreq
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
             resources: irq:24 ioport:e000(size=4096) memory:fd000000-fe0fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GM107 [GeForce GTX 750]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:46 memory:fd000000-fdffffff  memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128)  memory:fe000000-fe07ffff
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
                resources: irq:44 memory:fe080000-fe083fff
        *-pci:1
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port D)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24
        *-pci:2
             description: PCI bridge
             product: RD890 PCI to PCI bridge (NB-SB link)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-pci:3
             description: PCI bridge
             product: RD890 PCI to PCI bridge (external gfx1 port B)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: d
             bus info: pci@0000:00:0d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
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
             resources: irq:19 ioport:f040(size=8) ioport:f030(size=4)  ioport:f020(size=8) ioport:f010(size=4) ioport:f000(size=16)  memory:fe40b000-fe40b3ff
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
             resources: irq:18 memory:fe40a000-fe40afff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-25-generic ohci_hcd
                physical id: 1
                bus info: usb@8
                logical name: usb8
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
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
             resources: irq:17 memory:fe409000-fe4090ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-25-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
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
             resources: irq:20 memory:fe408000-fe408fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-25-generic ohci_hcd
                physical id: 1
                bus info: usb@9
                logical name: usb9
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
              *-usb
                   description: Keyboard
                   product: USB Keyboard
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@9:1
                   version: 64.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=90mA speed=2Mbit/s
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
             resources: irq:21 memory:fe407000-fe4070ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-25-generic ehci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.02
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
             resources: irq:16 memory:fe400000-fe403fff
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
        *-pci:4
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
             resources: irq:18 memory:fe406000-fe406fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-25-generic ohci_hcd
                physical id: 1
                bus info: usb@10
                logical name: usb10
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-pci:5
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
             resources: irq:20 ioport:d000(size=4096) memory:fe300000-fe3fffff
           *-storage
                description: SATA controller
                product: ASM1062 Serial ATA Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:42 ioport:d050(size=8)  ioport:d040(size=4) ioport:d030(size=8) ioport:d020(size=4)  ioport:d000(size=32) memory:fe300000-fe3001ff
        *-pci:6
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:20 memory:fe200000-fe2fffff
           *-usb
                description: USB controller
                product: ASM1042 SuperSpeed USB Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:21 memory:fe200000-fe207fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.2.0-25-generic xhci-hcd
                   physical id: 0
                   bus info: usb@2
                   logical name: usb2
                   version: 4.02
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.2.0-25-generic xhci-hcd
                   physical id: 1
                   bus info: usb@1
                   logical name: usb1
                   version: 4.02
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
        *-pci:7
             description: PCI bridge
             product: SB900 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:20 memory:fe100000-fe1fffff
           *-usb
                description: USB controller
                product: ASM1042 SuperSpeed USB Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:22 memory:fe100000-fe107fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.2.0-25-generic xhci-hcd
                   physical id: 0
                   bus info: usb@4
                   logical name: usb4
                   version: 4.02
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.2.0-25-generic xhci-hcd
                   physical id: 1
                   bus info: usb@3
                   logical name: usb3
                   version: 4.02
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
                 *-usb:0
                      description: Mouse
                      product: USB Device
                      vendor: Areson
                      physical id: 1
                      bus info: usb@3:1
                      version: 0.01
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
                 *-usb:1
                      description: Mass storage device
                      product: Android
                      vendor: Android
                      physical id: 2
                      bus info: usb@3:2
                      logical name: scsi8
                      version: ff.ff
                      serial: F4AZFG226865
                      capabilities: usb-2.00 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=500mA speed=480Mbit/s
                    *-cdrom
                         description: SCSI CD-ROM
                         physical id: 0.0.0
                         bus info: scsi@8:0.0.0
                         logical name: /dev/cdrom
                         logical name: /dev/sr0
                         logical name: /media/promet/cdrom_install
                         capabilities: audio
                         configuration: mount.fstype=udf  mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8  state=mounted status=ready
        *-pci:8
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
             resources: irq:20 ioport:c000(size=4096) ioport:d2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth1
                version: 09
                serial: 60:a4:4c:5f:0f:1a
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master  cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt  1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes  driver=r8169 driverversion=2.3LK-NAPI duplex=full  firmware=rtl8168f-1_0.0.5 06/18/12 ip=192.168.1.146 latency=0 link=yes  multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:c000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff
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
             resources: irq:22 memory:fe405000-fe405fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-25-generic ohci_hcd
                physical id: 1
                bus info: usb@11
                logical name: usb11
                version: 4.02
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
             resources: irq:23 memory:fe404000-fe4040ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-25-generic ehci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 4.02
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
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ADATA SP900
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 7b
             serial: 7E0320046961
             size: 119GiB (128GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=00066b61
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 5c4af77d-df05-49dd-8e35-33dfd5982567
                size: 119GiB
                capacity: 119GiB
                capabilities: primary bootable journaled  extended_attributes large_files huge_files dir_nlink extents ext4 ext2  initialized
                configuration: created=2014-03-24 00:25:23  filesystem=ext4 lastmountpoint=/ modified=2016-01-28 15:30:22  mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,data=ordered  mounted=2016-01-28 20:03:51 state=mounted
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ADATA SP900
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 7b
             serial: 7E0320044346
             size: 119GiB (128GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=37c9ea65
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: a4a39311-908e-a346-9f3f-c1cf53ccfb58
                size: 119GiB
                capacity: 119GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2014-03-25 01:49:29 filesystem=ntfs state=clean
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: virbr0-nic
       serial: 52:54:00:6d:a0:b3
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun  driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair  speed=10Mbit/s


```

This is on Ubuntu 15.10

Maybe to do with nvidia proprietary driver (NVIDIA-Linux-x86_64-352.55)? Though might not explain our mutual issue.

Just though I'd throw my hat into the ring. 

my eth1 wired interface was totally removed on my last reboot and  network-manager seems to have dissappeared from my Unity panel, dunno  what's up with that...

---

### Post by Stazzy on 2016-01-29
> my eth1 wired interface was totally removed on my last reboot and   network-manager seems to have dissappeared from my Unity panel, dunno   what's up with that...

I tried a few things here: [http://askubuntu.com/questions/230698/how-to-restart-the-networking-service](http://askubuntu.com/questions/230698/how-to-restart-the-networking-service) 
One of those worked after reboot, maybe ```
sudo killall NetworkManager
```. Well, at least until the next freeze. 


> Go back to the last old distro (boot it live from USB) that worked.  See if you still have the freezing problem.

Couldn't install Mint 13, don't know why. Now I'm testing an Ubuntu 12.04... well see...

---

### Post by Stazzy on 2016-01-31
> **weatherman2 said:**
> Go back to the last old distro (boot it live from USB) that worked.  See if you still have the freezing problem.  If you do, I suspect a hardware problem - one of two good possiblities:

1. Bad RAM.  Run Memtest for a good hour or more and see if you get any errors.  (Every Ubuntu boot USB includes Memtest in the menu - hit the Esc key as soon as the USB starts to boot to get a menu - after you choose the language.)  Yes, RAM does occasionally go bad.

2. Dirty CPU fan/heat sink and overheating.  This is very common on older laptops.  Often this will cause random shutdowns but could also cause freezing.  You'd be more likely to see this after the laptop has been on for a while vs. when it is cold.

Freezing continues no matter which distro. Now I'm using Ubuntu 12.04, wanted to see if older would be better. 
Memtest passed without errors, and freezing sometimes happens after having used the computer for a minute or so, it doesn't seem to be a pb with overheating. 

I may be utterly wrong, but I still suspect the wireless card. Because there's no freezing when I use cabled network, neither when wifi is shut down. And, the network-manager always dies and loses the wireless card after a freeze / hardboot.

...so... older kernel? Other version of network-manager? Other wireless drivers? Something completely else? 
There's a bug freezing computer when using wifi, but without a real solution: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1464738](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1464738)

---

