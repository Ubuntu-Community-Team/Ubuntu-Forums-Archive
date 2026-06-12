---
title: "Brightness control with FN keys doesnt work 14.04.03"
date: 2016-03-19
forum: Hardware
---

### Post by federico24 on 2016-03-19
Hello guys, i'm new on Ubuntu, the distribution does not work for my FN keys, can anyone can help me  to fix the problem?.

I have a notebook, is a Samsung NP470R5E-X01CL.

Redgards.

---

### Post by mörgæs on 2016-03-20
Hi, welcome to the fora.
Let's begin with seeing the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by federico24 on 2016-03-20
> **mörgæs said:**
> Hi, welcome to the fora.
Let's begin with seeing the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Thanks for the help.

```
computer    descripción: Portátil
    producto: 3570R/370R/470R/450R/510R/4450RV (SAMSUNG SENS Series)
    fabricante: SAMSUNG ELECTRONICS CO., LTD.
    versión: P15RAN
    serie: [REMOVED]
    anchura: 64 bits
    capacidades: smbios-2.7 dmi-2.7 vsyscall32
    configuración: boot=normal chassis=laptop family=SAMSUNG SENS sku=SAMSUNG SENS Series uuid=[REMOVED]
  *-core
       descripción: Placa base
       producto: NP470R5E-X01CL
       fabricante: SAMSUNG ELECTRONICS CO., LTD.
       id físico: 0
       versión: SEC_SW_REVISION_1234567890ABCD
       serie: [REMOVED]
       ranura: Middle
     *-firmware
          descripción: BIOS
          fabricante: American Megatrends Inc.
          id físico: 0
          versión: P15RAN.208.140429.ZW
          date: 04/29/2014
          tamaño: 64KiB
          capacidad: 4032KiB
          capacidades: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache:0
          descripción: L2 caché
          id físico: 34
          ranura: CPU Internal L2
          tamaño: 512KiB
          capacidad: 512KiB
          capacidades: internal write-through unified
     *-cache:1
          descripción: L1 caché
          id físico: 35
          ranura: CPU Internal L1
          tamaño: 128KiB
          capacidad: 128KiB
          capacidades: internal write-through data
     *-cache:2
          descripción: L3 caché
          id físico: 36
          ranura: CPU Internal L3
          tamaño: 3MiB
          capacidad: 3MiB
          capacidades: internal write-back unified
     *-memory
          descripción: Memoria de sistema
          id físico: 37
          ranura: Placa de sistema o placa base
          tamaño: 8GiB
        *-bank:0
             descripción: SODIMM DDR3 Síncrono 1600 MHz (0,6 ns)
             producto: M471B5273EB0-CK0
             fabricante: Samsung
             id físico: 0
             serie: [REMOVED]
             ranura: ChannelA-DIMM0
             tamaño: 4GiB
             anchura: 64 bits
             reloj: 1600MHz (0.6ns)
        *-bank:1
             descripción: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-11-10 11:11+0000X-Generator: Launchpad (build 17241) [vacío]
             producto: [Empty]
             fabricante: [Empty]
             id físico: 1
             serie: [REMOVED]
             ranura: ChannelA-DIMM1
        *-bank:2
             descripción: SODIMM DDR3 Síncrono 1600 MHz (0,6 ns)
             producto: M471B5273EB0-CK0
             fabricante: Samsung
             id físico: 2
             serie: [REMOVED]
             ranura: ChannelB-DIMM0
             tamaño: 4GiB
             anchura: 64 bits
             reloj: 1600MHz (0.6ns)
        *-bank:3
             descripción: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-11-10 11:11+0000X-Generator: Launchpad (build 17241) [vacío]
             producto: [Empty]
             fabricante: [Empty]
             id físico: 3
             serie: [REMOVED]
             ranura: ChannelB-DIMM1
     *-cpu
          descripción: CPU
          producto: Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz
          fabricante: Intel Corp.
          id físico: 38
          información del bus: cpu@0
          versión: Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz
          ranura: SOCKET 0
          tamaño: 3040MHz
          capacidad: 3800MHz
          anchura: 64 bits
          reloj: 100MHz
          capacidades: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt cpufreq
          configuración: cores=2 enabledcores=2 threads=4
     *-pci
          descripción: Host bridge
          producto: 3rd Gen Core processor DRAM Controller
          fabricante: Intel Corporation
          id físico: 100
          información del bus: pci@0000:00:00.0
          versión: 09
          anchura: 32 bits
          reloj: 33MHz
          configuración: driver=ivb_uncore
          recursos: irq:0
        *-pci:0
             descripción: PCI bridge
             producto: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             fabricante: Intel Corporation
             id físico: 1
             información del bus: pci@0000:00:01.0
             versión: 09
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pm msi pciexpress normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:26 ioport:e000(size=4096) memoria:f7d00000-f7dfffff ioport:e0000000(size=268435456)
           *-display
                descripción: Display controller
                producto: Mars [Radeon HD 8670A/8670M/8750M]
                fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
                id físico: 0
                información del bus: pci@0000:01:00.0
                versión: 00
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm pciexpress msi bus_master cap_list rom
                configuración: driver=radeon latency=0
                recursos: irq:33 memoria:e0000000-efffffff memoria:f7d00000-f7d3ffff ioport:e000(size=256) memoria:f7d40000-f7d5ffff
        *-display
             descripción: VGA compatible controller
             producto: 3rd Gen Core processor Graphics Controller
             fabricante: Intel Corporation
             id físico: 2
             información del bus: pci@0000:00:02.0
             versión: 09
             anchura: 64 bits
             reloj: 33MHz
             capacidades: msi pm vga_controller bus_master cap_list rom
             configuración: driver=i915 latency=0
             recursos: irq:31 memoria:f7800000-f7bfffff memoria:d0000000-dfffffff ioport:f000(size=64)
        *-usb:0
             descripción: USB controller
             producto: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             fabricante: Intel Corporation
             id físico: 14
             información del bus: pci@0000:00:14.0
             versión: 04
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi xhci bus_master cap_list
             configuración: driver=xhci_hcd latency=0
             recursos: irq:27 memoria:f7e00000-f7e0ffff
        *-communication
             descripción: Communication controller
             producto: 7 Series/C210 Series Chipset Family MEI Controller #1
             fabricante: Intel Corporation
             id físico: 16
             información del bus: pci@0000:00:16.0
             versión: 04
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi bus_master cap_list
             configuración: driver=mei_me latency=0
             recursos: irq:30 memoria:f7e1a000-f7e1a00f
        *-usb:1
             descripción: USB controller
             producto: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             fabricante: Intel Corporation
             id físico: 1a
             información del bus: pci@0000:00:1a.0
             versión: 04
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuración: driver=ehci-pci latency=0
             recursos: irq:16 memoria:f7e18000-f7e183ff
        *-multimedia
             descripción: Audio device
             producto: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             fabricante: Intel Corporation
             id físico: 1b
             información del bus: pci@0000:00:1b.0
             versión: 04
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuración: driver=snd_hda_intel latency=0
             recursos: irq:32 memoria:f7e10000-f7e13fff
        *-pci:1
             descripción: PCI bridge
             producto: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             fabricante: Intel Corporation
             id físico: 1c
             información del bus: pci@0000:00:1c.0
             versión: c4
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:16 ioport:2000(size=4096) memoria:f7c00000-f7cfffff ioport:cfb00000(size=2097152)
           *-network
                descripción: Interfaz inalámbrica
                producto: AR9485 Wireless Network Adapter
                fabricante: Qualcomm Atheros
                id físico: 0
                información del bus: pci@0000:02:00.0
                nombre lógico: wlan0
                versión: 01
                serie: [REMOVED]
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuración: broadcast=yes driver=ath9k driverversion=3.19.0-56-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                recursos: irq:16 memoria:f7c00000-f7c7ffff memoria:f7c80000-f7c8ffff
        *-pci:2
             descripción: PCI bridge
             producto: 7 Series/C210 Series Chipset Family PCI Express Root Port 4
             fabricante: Intel Corporation
             id físico: 1c.3
             información del bus: pci@0000:00:1c.3
             versión: c4
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:19 ioport:d000(size=4096) memoria:f0100000-f04fffff ioport:f0000000(size=1048576)
           *-network
                descripción: Ethernet interface
                producto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                fabricante: Realtek Semiconductor Co., Ltd.
                id físico: 0
                información del bus: pci@0000:03:00.0
                nombre lógico: eth0
                versión: 06
                serie: [REMOVED]
                tamaño: 10Mbit/s
                capacidad: 1Gbit/s
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                recursos: irq:28 ioport:d000(size=256) memoria:f0004000-f0004fff memoria:f0000000-f0003fff
        *-usb:2
             descripción: USB controller
             producto: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             fabricante: Intel Corporation
             id físico: 1d
             información del bus: pci@0000:00:1d.0
             versión: 04
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuración: driver=ehci-pci latency=0
             recursos: irq:23 memoria:f7e17000-f7e173ff
        *-isa
             descripción: ISA bridge
             producto: HM76 Express Chipset LPC Controller
             fabricante: Intel Corporation
             id físico: 1f
             información del bus: pci@0000:00:1f.0
             versión: 04
             anchura: 32 bits
             reloj: 33MHz
             capacidades: isa bus_master cap_list
             configuración: driver=lpc_ich latency=0
             recursos: irq:0
        *-storage
             descripción: SATA controller
             producto: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             fabricante: Intel Corporation
             id físico: 1f.2
             información del bus: pci@0000:00:1f.2
             versión: 04
             anchura: 32 bits
             reloj: 66MHz
             capacidades: storage msi pm ahci_1.0 bus_master cap_list
             configuración: driver=ahci latency=0
             recursos: irq:29 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memoria:f7e16000-f7e167ff
        *-serial NO RECLAMADO
             descripción: SMBus
             producto: 7 Series/C210 Series Chipset Family SMBus Controller
             fabricante: Intel Corporation
             id físico: 1f.3
             información del bus: pci@0000:00:1f.3
             versión: 04
             anchura: 64 bits
             reloj: 33MHz
             configuración: latency=0
             recursos: memoria:f7e15000-f7e150ff ioport:f040(size=32)
     *-scsi
          id físico: 1
          nombre lógico: scsi0
          capacidades: emulated
        *-disk
             descripción: ATA Disk
             producto: ST1000LM024 HN-M
             fabricante: Seagate
             id físico: 0.0.0
             información del bus: scsi@0:0.0.0
             nombre lógico: /dev/sda
             versión: 0002
             serie: [REMOVED]
             tamaño: 931GiB (1TB)
             capacidades: gpt-1.00 partitioned partitioned:gpt
             configuración: ansiversion=5 guid=a62d0ea2-18b4-4707-856a-1f56fed6e3da sectorsize=4096
           *-volume:0
                descripción: Linux swap volumen
                fabricante: Linux
                id físico: 1
                información del bus: scsi@0:0.0.0,1
                nombre lógico: /dev/sda1
                versión: 1
                serie: [REMOVED]
                tamaño: 11GiB
                capacidad: 11GiB
                capacidades: nofs swap initialized
                configuración: filesystem=swap pagesize=4095
           *-volume:1
                descripción: Windows FAT volumen
                fabricante: mkfs.fat
                id físico: 2
                información del bus: scsi@0:0.0.0,2
                nombre lógico: /dev/sda2
                nombre lógico: /boot/efi
                versión: FAT32
                serie: [REMOVED]
                tamaño: 87MiB
                capacidad: 94MiB
                capacidades: boot fat initialized
                configuración: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:2
                descripción: partición EXT4
                fabricante: Linux
                id físico: 3
                información del bus: scsi@0:0.0.0,3
                nombre lógico: /dev/sda3
                nombre lógico: /
                versión: 1.0
                serie: [REMOVED]
                tamaño: 190GiB
                capacidad: 190GiB
                capacidades: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuración: created=2016-03-16 22:44:51 filesystem=ext4 lastmountpoint=/ modified=2016-03-19 20:29:50 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-03-19 20:29:50 state=mounted
           *-volume:3
                descripción: Windows NTFS volumen
                fabricante: Windows
                id físico: 4
                información del bus: scsi@0:0.0.0,4
                nombre lógico: /dev/sda4
                versión: 3.1
                serie: [REMOVED]
                tamaño: 729GiB
                capacidad: 729GiB
                capacidades: ntfs initialized
                configuración: clustersize=4096 created=2016-03-16 23:31:25 filesystem=ntfs label=Respaldo state=clean
  *-power NO RECLAMADO
       descripción: To Be Filled By O.E.M.
       producto: To Be Filled By O.E.M.
       fabricante: To Be Filled By O.E.M.
       id físico: 1
       versión: To Be Filled By O.E.M.
       serie: [REMOVED]
       capacidad: 32768mWh
```

---

### Post by mörgæs on 2016-03-21
Your processor belongs to the Ivy Bridge family which is not well supported by old releases like 14.04. 
I recommend a fresh install of 15.10 or the almost-finished 16.04.

---

### Post by federico24 on 2016-03-22
Thankyou, Ubuntu 15.10 It's was works with a clean instalation.
Readgards

---

### Post by mörgæs on 2016-03-23
Yes, 14.04 is often the problem, not the solution. 

Please mark the thread solved.

---

