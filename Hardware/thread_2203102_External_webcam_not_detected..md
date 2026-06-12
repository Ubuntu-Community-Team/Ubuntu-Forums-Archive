---
title: "External webcam not detected."
date: 2014-02-01
forum: Hardware
---

### Post by yoramdavid on 2014-02-01
Hello,

I have a Lubuntu 13.10 installed on a HP Pavillon dv6000.
I just bought a new webcam, Make is Growing, model is "Impala PC Camera".
I want to use it with skype, but it is not detected at all.
Any help would be appreciated.

The following command gave those results:

```
lsmod |grep uvcvideo 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core

```

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:048e Holtek Semiconductor, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:048e Holtek Semiconductor, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
sudo lshw
bart-hp-pavilion-dv6000-rt118ea-ab9
    descrição: Notebook
    produto: HP Pavilion dv6000 (RT118EA#AB9) (RT118EA#AB9)
    fabricante: Hewlett-Packard
    versão: Rev 1
    serial: CNF6483K8F
    largura: 32 bits
    capacidades: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuração: boot=oem-specific chassis=notebook cpus=2 family=103C_5335KV sku=RT118EA#AB9 uuid=434E4637-3134-3144-4A53-001B24144B84
  *-core
       descrição: Placa-mãe
       produto: 30BB
       fabricante: Quanta
       ID físico: 0
       versão: 66.42
       serial: None
     *-firmware
          descrição: BIOS
          fabricante: Hewlett-Packard
          ID físico: 0
          versão: F.2D
          date: 11/26/2008
          tamanho: 100KiB
          capacidade: 960KiB
          capacidades: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          descrição: CPU
          produto: Genuine Intel(R) CPU           T2250  @ 1.73GHz
          fabricante: Intel Corp.
          ID físico: 4
          informações do barramento: cpu@0
          versão: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U2E1
          tamanho: 1733MHz
          capacidade: 1733MHz
          largura: 32 bits
          clock: 533MHz
          capacidades: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor est tm2 xtpr pdcm dtherm cpufreq
          configuração: id=0
        *-cache:0
             descrição: L1 cache
             ID físico: 5
             slot: L1 Cache
             tamanho: 32KiB
             capacidade: 32KiB
             capacidades: asynchronous internal write-back
        *-cache:1
             descrição: L2 cache
             ID físico: 6
             slot: L2 Cache
             tamanho: 2MiB
             capacidade: 2MiB
             capacidades: burst external write-back
        *-logicalcpu:0
             descrição: CPU lógico
             ID físico: 0.1
             largura: 32 bits
             capacidades: logical
        *-logicalcpu:1
             descrição: CPU lógico
             ID físico: 0.2
             largura: 32 bits
             capacidades: logical
     *-memory
          descrição: Memória do sistema
          ID físico: d
          slot: Placa do sistema ou placa-mãe
          tamanho: 1GiB
          capacidade: 2GiB
        *-bank:0
             descrição: DIMM DDR2 Síncrono 533 MHz (1,9 ns)
             ID físico: 0
             slot: DIMM 1
             tamanho: 512MiB
             largura: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             descrição: DIMM DDR2 Síncrono 533 MHz (1,9 ns)
             ID físico: 1
             slot: DIMM 2
             tamanho: 512MiB
             largura: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu:1
          ID físico: 1
          informações do barramento: cpu@1
          versão: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          tamanho: 800MHz
          capacidade: 800MHz
          capacidades: ht cpufreq
          configuração: id=0
        *-logicalcpu:0
             descrição: CPU lógico
             ID físico: 0.1
             capacidades: logical
        *-logicalcpu:1
             descrição: CPU lógico
             ID físico: 0.2
             capacidades: logical
     *-pci
          descrição: Host bridge
          produto: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          fabricante: Intel Corporation
          ID físico: 100
          informações do barramento: pci@0000:00:00.0
          versão: 03
          largura: 32 bits
          clock: 33MHz
          configuração: driver=agpgart-intel
          recursos: irq:0
        *-display:0
             descrição: VGA compatible controller
             produto: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             fabricante: Intel Corporation
             ID físico: 2
             informações do barramento: pci@0000:00:02.0
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: msi pm vga_controller bus_master cap_list rom
             configuração: driver=i915 latency=0
             recursos: irq:16 memória:d8100000-d817ffff porta de E/S:1800(tamanho=8) memória:c0000000-cfffffff memória:d8200000-d823ffff
        *-display:1 DISPONÍVEL
             descrição: Display controller
             produto: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             fabricante: Intel Corporation
             ID físico: 2.1
             informações do barramento: pci@0000:00:02.1
             versão: 03
             largura: 32 bits
             clock: 33MHz
             capacidades: pm bus_master cap_list
             configuração: latency=0
             recursos: memória:d8180000-d81fffff
        *-multimedia
             descrição: Audio device
             produto: NM10/ICH7 Family High Definition Audio Controller
             fabricante: Intel Corporation
             ID físico: 1b
             informações do barramento: pci@0000:00:1b.0
             versão: 02
             largura: 64 bits
             clock: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuração: driver=snd_hda_intel latency=0
             recursos: irq:44 memória:d8240000-d8243fff
        *-pci:0
             descrição: PCI bridge
             produto: NM10/ICH7 Family PCI Express Port 1
             fabricante: Intel Corporation
             ID físico: 1c
             informações do barramento: pci@0000:00:1c.0
             versão: 02
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:40 porta de E/S:2000(tamanho=4096) memória:d6000000-d7ffffff porta de E/S:d2000000(tamanho=33554432)
           *-network DESABILITADO
                descrição: Interface sem fio
                produto: PRO/Wireless 3945ABG [Golan] Network Connection
                fabricante: Intel Corporation
                ID físico: 0
                informações do barramento: pci@0000:02:00.0
                nome lógico: wlan0
                versão: 02
                serial: 00:18:de:c4:ac:47
                largura: 32 bits
                clock: 33MHz
                capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuração: broadcast=yes driver=iwl3945 driverversion=3.11.0-15-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
                recursos: irq:43 memória:d6000000-d6000fff
        *-pci:1
             descrição: PCI bridge
             produto: NM10/ICH7 Family PCI Express Port 2
             fabricante: Intel Corporation
             ID físico: 1c.1
             informações do barramento: pci@0000:00:1c.1
             versão: 02
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:41 porta de E/S:3000(tamanho=4096) memória:d4000000-d5ffffff porta de E/S:d0000000(tamanho=33554432)
        *-usb:0
             descrição: USB controller
             produto: NM10/ICH7 Family USB UHCI Controller #1
             fabricante: Intel Corporation
             ID físico: 1d
             informações do barramento: pci@0000:00:1d.0
             versão: 02
             largura: 32 bits
             clock: 33MHz
             capacidades: uhci bus_master
             configuração: driver=uhci_hcd latency=0
             recursos: irq:23 porta de E/S:1820(tamanho=32)
        *-usb:1
             descrição: USB controller
             produto: NM10/ICH7 Family USB UHCI Controller #2
             fabricante: Intel Corporation
             ID físico: 1d.1
             informações do barramento: pci@0000:00:1d.1
             versão: 02
             largura: 32 bits
             clock: 33MHz
             capacidades: uhci bus_master
             configuração: driver=uhci_hcd latency=0
             recursos: irq:19 porta de E/S:1840(tamanho=32)
        *-usb:2
             descrição: USB controller
             produto: NM10/ICH7 Family USB UHCI Controller #3
             fabricante: Intel Corporation
             ID físico: 1d.2
             informações do barramento: pci@0000:00:1d.2
             versão: 02
             largura: 32 bits
             clock: 33MHz
             capacidades: uhci bus_master
             configuração: driver=uhci_hcd latency=0
             recursos: irq:18 porta de E/S:1860(tamanho=32)
        *-usb:3
             descrição: USB controller
             produto: NM10/ICH7 Family USB UHCI Controller #4
             fabricante: Intel Corporation
             ID físico: 1d.3
             informações do barramento: pci@0000:00:1d.3
             versão: 02
             largura: 32 bits
             clock: 33MHz
             capacidades: uhci bus_master
             configuração: driver=uhci_hcd latency=0
             recursos: irq:16 porta de E/S:1880(tamanho=32)
        *-usb:4
             descrição: USB controller
             produto: NM10/ICH7 Family USB2 EHCI Controller
             fabricante: Intel Corporation
             ID físico: 1d.7
             informações do barramento: pci@0000:00:1d.7
             versão: 02
             largura: 32 bits
             clock: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuração: driver=ehci-pci latency=0
             recursos: irq:23 memória:d8444000-d84443ff
        *-pci:2
             descrição: PCI bridge
             produto: 82801 Mobile PCI Bridge
             fabricante: Intel Corporation
             ID físico: 1e
             informações do barramento: pci@0000:00:1e.0
             versão: e2
             largura: 32 bits
             clock: 33MHz
             capacidades: pci subtractive_decode bus_master cap_list
             recursos: porta de E/S:4000(tamanho=4096) memória:d8000000-d80fffff
           *-firewire
                descrição: FireWire (IEEE 1394)
                produto: R5C832 IEEE 1394 Controller
                fabricante: Ricoh Co Ltd
                ID físico: 5
                informações do barramento: pci@0000:05:05.0
                versão: 00
                largura: 32 bits
                clock: 33MHz
                capacidades: pm ohci bus_master cap_list
                configuração: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                recursos: irq:16 memória:d8001000-d80017ff
           *-generic:0
                descrição: SD Host controller
                produto: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                fabricante: Ricoh Co Ltd
                ID físico: 5.1
                informações do barramento: pci@0000:05:05.1
                versão: 19
                largura: 32 bits
                clock: 33MHz
                capacidades: pm bus_master cap_list
                configuração: driver=sdhci-pci latency=64
                recursos: irq:17 memória:d8001800-d80018ff
           *-generic:1
                descrição: System peripheral
                produto: R5C592 Memory Stick Bus Host Adapter
                fabricante: Ricoh Co Ltd
                ID físico: 5.2
                informações do barramento: pci@0000:05:05.2
                versão: 0a
                largura: 32 bits
                clock: 33MHz
                capacidades: pm cap_list
                configuração: driver=r592 latency=0
                recursos: irq:17 memória:d8002000-d80020ff
           *-generic:2
                descrição: System peripheral
                produto: xD-Picture Card Controller
                fabricante: Ricoh Co Ltd
                ID físico: 5.3
                informações do barramento: pci@0000:05:05.3
                versão: 05
                largura: 32 bits
                clock: 33MHz
                capacidades: pm cap_list
                configuração: driver=r852 latency=0
                recursos: irq:17 memória:d8002400-d80024ff
           *-network
                descrição: Ethernet interface
                produto: PRO/100 VE Network Connection
                fabricante: Intel Corporation
                ID físico: 8
                informações do barramento: pci@0000:05:08.0
                nome lógico: eth0
                versão: 02
                serial: 00:1b:24:14:4b:84
                tamanho: 100Mbit/s
                capacidade: 100Mbit/s
                largura: 32 bits
                clock: 33MHz
                capacidades: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuração: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.10.5 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                recursos: irq:20 memória:d8000000-d8000fff porta de E/S:4000(tamanho=64)
        *-isa
             descrição: ISA bridge
             produto: 82801GBM (ICH7-M) LPC Interface Bridge
             fabricante: Intel Corporation
             ID físico: 1f
             informações do barramento: pci@0000:00:1f.0
             versão: 02
             largura: 32 bits
             clock: 33MHz
             capacidades: isa bus_master cap_list
             configuração: driver=lpc_ich latency=0
             recursos: irq:0
        *-ide
             descrição: IDE interface
             produto: 82801G (ICH7 Family) IDE Controller
             fabricante: Intel Corporation
             ID físico: 1f.1
             informações do barramento: pci@0000:00:1f.1
             versão: 02
             largura: 32 bits
             clock: 33MHz
             capacidades: ide bus_master
             configuração: driver=ata_piix latency=0
             recursos: irq:18 porta de E/S:1f0(tamanho=8) porta de E/S:3f6 porta de E/S:170(tamanho=8) porta de E/S:376 porta de E/S:1810(tamanho=16)
        *-storage
             descrição: SATA controller
             produto: 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode]
             fabricante: Intel Corporation
             ID físico: 1f.2
             informações do barramento: pci@0000:00:1f.2
             versão: 02
             largura: 32 bits
             clock: 66MHz
             capacidades: storage msi pm ahci_1.0 bus_master cap_list
             configuração: driver=ahci latency=0
             recursos: irq:42 porta de E/S:18d0(tamanho=8) porta de E/S:18c4(tamanho=4) porta de E/S:18c8(tamanho=8) porta de E/S:18c0(tamanho=4) porta de E/S:18b0(tamanho=16) memória:d8444400-d84447ff
        *-serial DISPONÍVEL
             descrição: SMBus
             produto: NM10/ICH7 Family SMBus Controller
             fabricante: Intel Corporation
             ID físico: 1f.3
             informações do barramento: pci@0000:00:1f.3
             versão: 02
             largura: 32 bits
             clock: 33MHz
             configuração: latency=0
             recursos: porta de E/S:18e0(tamanho=32)
     *-scsi:0
          ID físico: 2
          nome lógico: scsi0
          capacidades: emulated
        *-cdrom
             descrição: DVD-RAM writer
             produto: DVD-RAM SDVD8821
             fabricante: PHILIPS
             ID físico: 0.0.0
             informações do barramento: scsi@0:0.0.0
             nome lógico: /dev/cdrom
             nome lógico: /dev/sr0
             versão: EH19
             capacidades: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuração: ansiversion=5 status=nodisc
     *-scsi:1
          ID físico: 3
          nome lógico: scsi2
          capacidades: emulated
        *-disk
             descrição: ATA Disk
             produto: FUJITSU MHV2120B
             fabricante: Fujitsu
             ID físico: 0.0.0
             informações do barramento: scsi@2:0.0.0
             nome lógico: /dev/sda
             versão: 892C
             serial: NW9XT6B2SCMU
             tamanho: 111GiB (120GB)
             capacidades: partitioned partitioned:dos
             configuração: ansiversion=5 sectorsize=512 signature=00014154
           *-volume:0
                descrição: volume EXT4
                fabricante: Linux
                ID físico: 1
                informações do barramento: scsi@2:0.0.0,1
                nome lógico: /dev/sda1
                nome lógico: /
                versão: 1.0
                serial: 3711b770-e9ff-41ce-9b28-3b19982f2fd6
                tamanho: 55GiB
                capacidade: 55GiB
                capacidades: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuração: created=2013-04-30 11:25:26 filesystem=ext4 lastmountpoint=/ modified=2014-02-01 20:40:38 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-02-01 20:40:38 state=mounted
           *-volume:1
                descrição: Extended partition
                ID físico: 2
                informações do barramento: scsi@2:0.0.0,2
                nome lógico: /dev/sda2
                tamanho: 56GiB
                capacidade: 56GiB
                capacidades: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   descrição: Linux swap / Solaris partition
                   ID físico: 5
                   nome lógico: /dev/sda5
                   capacidade: 1012MiB
                   capacidades: nofs
              *-logicalvolume:1
                   descrição: Linux filesystem partition
                   ID físico: 6
                   nome lógico: /dev/sda6
                   capacidade: 55GiB
bart@bart-HP-Pavilion-dv6000-RT118EA-AB9:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
bart@bart-HP-Pavilion-dv6000-RT118EA-AB9:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:048e Holtek Semiconductor, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

