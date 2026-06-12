---
title: "Notebook acer, wifi dejo de funcionar"
date: 2011-02-26
forum: Hardware
---

### Post by fedebaka on 2011-02-26
Hola! Quisiera pedir ayuda.

Tengo una notebook acer 5551-4931 y instale ubuntu 10.10. Luego usando los drivers privativos se instaló el driver de wifi (controlador inalambrico broadcom sta) y anduvo muy bien por unos dias. Pero ahora de un dia para el otro arranco y no funciona. La notebook tiene una lucecita anaranjada que muestra si la placa wifi está encendida, que está apagada. Apretar la combinacion de teclas que supuestamente la enciende no funciona (nunca necesité apretarla porque siempre estaba encendida al arrancar). En el area de notificacion, en el icono de red, sale "redes inalambricas: desconectado". Si pongo "sudo ifconfig wlan0 up" (algo que encontre en foros) sale "error: no existe el dispositivo". Desinstale y volvi a instalar el driver pero sigue igual. Aclaro que en la misma notebook con windows 7 funciona bien.

Alguien me ayuda? Gracias!

---

### Post by guillermolisi on 2011-02-26
Si podes, abri una terminal e ingresa los siguientes comandos, copiando las salidas de cada uno para luego mostrarlas aqui, asi sabremos exactamente como se esta reconociendo el hardware:
```
sudo lspci
```
```
sudo lsusb
```
```
sudo lshw
```
```
sudo lsmod
```

---

### Post by fedebaka on 2011-02-26
Gracias por responder! ahi va
[spoiler]```
sudo lspci

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
08:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

``````
sudo lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0402:9665 ALi Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
sudo lshw

mewtwo                    
    description: Notebook
    product: Aspire 5551
    vendor: Acer
    version: V1.06
    serial: LXPWK021590290E5461601
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=8EE597B4-2943-591C-2EFA-88AE1D6701EC
  *-core
       description: Motherboard
       product: Aspire 5551
       vendor: Acer
       physical id: 0
       version: V1.06
       serial: LXPWK021590290E5461601
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.06 (06/01/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: AMD Turion(tm) II P520 Dual-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 20
          bus info: cpu@0
          version: AMD Turion(tm) II P520 Dual-Core Processor
          serial: NotSupport
          slot: Socket S1G4
          size: 2300MHz
          capacity: 2300MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
        *-cache:0 DISABLED
             description: L1 cache
             physical id: 21
             slot: L1 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
        *-cache:1 DISABLED
             description: L1 cache
             physical id: 22
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-through unified
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 1066 MHz (0.9 ns)
             product: M471B5673FH0-CH9
             vendor: Samsung
             physical id: 0
             serial: 95BEE52D
             slot: DIMM0
             size: 2GiB
             width: 8 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM Synchronous 1066 MHz (0.9 ns)
             product: M471B5673FH0-CH9
             vendor: Samsung
             physical id: 1
             serial: 95BEE536
             slot: DIMM1
             size: 2GiB
             width: 8 bits
             clock: 1066MHz (0.9ns)
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge Alternate
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (int gfx)
             vendor: Advanced Micro Devices [AMD]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:6000(size=4096) memory:f2100000-f22fffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: M880G [Mobility Radeon HD 4200]
                vendor: ATI Technologies Inc
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
                product: RS880 Audio Device [Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:f2210000-f2213fff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
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
                serial: 88:ae:1d:67:01:ec
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=sb ip=192.168.11.10 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:43 memory:f1100000-f110ffff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
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
                product: BCM43225 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth1
                version: 01
                serial: c4:46:19:5e:f4:a6
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f1000000-f1003fff
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:42 ioport:7038(size=8) ioport:704c(size=4) ioport:7030(size=8) ioport:7048(size=4) ioport:7010(size=16) memory:f2307000-f23073ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54505
                vendor: Hitachi
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: PB4O
                serial: 100619PBN40317DXLYNE
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2173d8e6
              *-volume:0
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   size: 23GiB
                   capacity: 23GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4094MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 20GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: a76fa613-7210-470f-adf5-33f86c26b016
                   size: 50GiB
                   capacity: 50GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-12-09 23:13:49 filesystem=ntfs label=Mewtwo state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 85d6ed3a-83cf-4e67-a66d-9fd0d8cccdab
                   size: 391GiB
                   capacity: 391GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-12-04 19:52:15 filesystem=ntfs label=Archivos state=clean
           *-cdrom
                description: DVD-RAM writer
                product: BDDVDRW CT21N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f2306000-f2306fff
        *-usb:1
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f2307500-f23075ff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f2305000-f2305fff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f2307400-f23074ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 41
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:7000(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f2300000-f2303fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
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
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:4
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f2304000-f2304fff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
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
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

``````
sudo lsmod

Module                  Size  Used by
joydev                 11395  0 
parport_pc             30086  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_realtek   300173  1 
snd_hda_intel          26115  2 
snd_hda_codec         100919  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2523725  34 
lib80211_crypt_tkip     8732  0 
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                62080  0 
edac_core              46822  0 
wl                   1965231  0 
k10temp                 3535  0 
edac_mce_amd            9387  0 
serio_raw               4910  0 
lib80211                6175  2 lib80211_crypt_tkip,wl
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
i2c_piix4              10047  0 
shpchp                 34910  0 
video                  22176  0 
output                  2527  1 video
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   22210  2 
tg3                   135768  0 
libahci                26148  1 ahci
pata_atiixp             4405  0 

```[/spoiler]

A propósito, cuando enchufo el cable de red anda bien (eth0).

---

### Post by fedebaka on 2011-03-12
un up! a ver si alguin me ayuda :(

---

### Post by guillermolisi on 2011-03-12
Ya he visto varios casos similares con placas WiFi Broadcom y si no me equivoco hay por lo menos un thread solucionado (hace algunos pocos dias atras) al respecto en este subforo.

---

