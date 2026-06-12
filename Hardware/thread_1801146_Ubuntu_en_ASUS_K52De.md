---
title: "Ubuntu en ASUS K52De"
date: 2011-07-10
forum: Hardware
---

### Post by anforguiven on 2011-07-10
Hola a todos, tengo problemas corriendo Ubuntu en mi ASUS K52De, no funcionan la suspencion, la ivernacion y el mayor problema es la pantalla que si queda en reposo al reactivarse titila como si tubiera problemas la retroiluminacion. Esto me sucede con todas las distros que probe, pero con windows los problemas desaparecen.Luego de buscar documentacion por todos lados me encuentro con la sorpresa de que no existe documentacion para mi notebook (por lo menos que funcione), probe con el ultimo kernel,con drivers privativos ATI y nada soluciona el problema con la pantalla que es lo mas grave. Espero que alguien sepa como puedo solucionar esto, saludos!!!

---

### Post by anforguiven on 2011-12-10
> **anforguiven said:**
> Hola a todos, tengo problemas corriendo Ubuntu en mi ASUS K52De, no funcionan la suspencion, la ivernacion y el mayor problema es la pantalla que si queda en reposo al reactivarse titila como si tubiera problemas la retroiluminacion. Esto me sucede con todas las distros que probe, pero con windows los problemas desaparecen.Luego de buscar documentacion por todos lados me encuentro con la sorpresa de que no existe documentacion para mi notebook (por lo menos que funcione), probe con el ultimo kernel,con drivers privativos ATI y nada soluciona el problema con la pantalla que es lo mas grave. Espero que alguien sepa como puedo solucionar esto, saludos!!!

Por favor alguien tiene que saber algo sobre este problema. Acabo de probar Ubuntu 11.10 y sigue pasando lo mismo!!!

---

### Post by guillermolisi on 2011-12-10
Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

---

### Post by anforguiven on 2011-12-10
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

Antes que nada no tengo palabras para agradecer tu tiempo,ya estoy reinstalando mi querido Ubuntu ya que lo borre por miedo a estropear el monitor o algo.
Apenas este todo en condiciones sigo tus indicaciones!

---

### Post by anforguiven on 2011-12-10
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

sudo lshw

asus                      
    description: Notebook
    product: K52De ()
    vendor: ASUSTeK Computer Inc.
    version: 1.0
    serial: B2N0AS15171907
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=006F86F3-BA3D-E081-3575-BCAEC5647FAB
  *-core
       description: Motherboard
       product: K52De
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: K52De.208
          date: 12/10/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II N830 Triple-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II N830 Triple-Core Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 3698MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=3 enabledcores=3
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 384KiB
             capacity: 384KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1536KiB
             capacity: 1536KiB
             capabilities: internal varies data
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 0
             serial: 66B2BFB0
             slot: A1_DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 1
             serial: 66B2BFAF
             slot: A1_DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fdf00000-fe8fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Manhattan [Mobility Radeon HD 5400 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:44 memory:d0000000-dfffffff memory:fdf20000-fdf3ffff ioport:e000(size=256) memory:fdf00000-fdf1ffff
           *-multimedia
                description: Audio device
                product: Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:45 memory:fdf40000-fdf43fff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:fea00000-feafffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 01
                serial: 48:5d:60:b3:4b:3b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.0.0-14-generic firmware=N/A ip=192.168.43.127 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:fea00000-fea0ffff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:fe900000-fe9fffff
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:fe907000-fe9070ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:05:00.2
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:fe906000-fe9060ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:05:00.3
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:18 memory:fe905000-fe9050ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:05:00.4
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:fe904000-fe9040ff
           *-network
                description: Ethernet interface
                product: JMC250 PCI Express Gigabit Ethernet Controller
                vendor: JMicron Technology Corp.
                physical id: 0.5
                bus info: pci@0000:05:00.5
                logical name: eth0
                version: 03
                serial: bc:ae:c5:64:7f:ab
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:46 memory:fe900000-fe903fff ioport:d100(size=128) ioport:d000(size=256)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:43 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:feb0a000-feb0a3ff
           *-disk
                description: ATA Disk
                product: SAMSUNG HN-M101M
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 2AR1
                serial: S2R8J9FB600108
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009b92c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: a1e12e24-2fc2-4e92-86a3-7a655eb37ab6
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-12-10 20:45:56 filesystem=ext4 lastmountpoint=/ modified=2011-12-10 21:18:29 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-12-10 21:19:32 state=mounted
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /home
                   version: 1.0
                   serial: 0911cb9d-a154-4a63-a5b1-617d34467442
                   size: 910GiB
                   capacity: 910GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-12-10 20:45:59 filesystem=ext4 lastmountpoint=/home modified=2011-12-11 01:11:36 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered mounted=2011-12-11 01:11:36 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 1952MiB
                   capacity: 1952MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1952MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT34N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AS00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb09000-feb09fff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb08000-feb080ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb07000-feb07fff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb06000-feb060ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
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
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:feb00000-feb03fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
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
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb05000-feb05fff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb04000-feb040ff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
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
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by anforguiven on 2011-12-10
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

 lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
05:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)

---

### Post by anforguiven on 2011-12-10
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

/var/log/dmesg (parte 1)
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=a1e12e24-2fc2-4e92-86a3-7a655eb37ab6 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afcc3000 (usable)
[    0.000000]  BIOS-e820: 00000000afcc3000 - 00000000afd0d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd0d000 - 00000000afd1b000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afd1b000 - 00000000afd2c000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd2c000 - 00000000afd34000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd34000 - 00000000afd44000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd44000 - 00000000afd45000 (usable)
[    0.000000]  BIOS-e820: 00000000afd45000 - 00000000afd47000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd47000 - 00000000afd48000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd48000 - 00000000afd4b000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd4b000 - 00000000afd51000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd51000 - 00000000afd71000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd71000 - 00000000afd72000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd72000 - 00000000afd87000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd87000 - 00000000afd8e000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd8e000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed61000 - 00000000fed71000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed80000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100001000 - 0000000150000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: ASUSTeK Computer Inc.         K52De/K52De, BIOS K52De.208 12/10/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x150000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF00000000 write-back
[    0.000000]   1 base 0000AFF00000 mask FFFFFFF00000 uncachable
[    0.000000]   2 base 0000B0000000 mask FFFFF0000000 uncachable
[    0.000000]   3 base 0000C0000000 mask FFFFC0000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000150000000 aka 5376M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 2815MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2816MB, range: 256MB, type UC
[    0.000000] reg 3, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 2815M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2815MB, range: 1MB, type UC
[    0.000000] e820 update range: 00000000aff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000aff00000
[    0.000000]  0000000000 - 0080000000 page 1G
[    0.000000]  0080000000 - 00afe00000 page 2M
[    0.000000]  00afe00000 - 00aff00000 page 4k
[    0.000000] kernel direct mapping tables up to aff00000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000150000000
[    0.000000]  0100000000 - 0140000000 page 1G
[    0.000000]  0140000000 - 0150000000 page 2M
[    0.000000] kernel direct mapping tables up to 150000000 @ afefe000-aff00000
[    0.000000] RAMDISK: 365b0000 - 372d0000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v03 _ASUS_)
[    0.000000] ACPI: XSDT 00000000afd0d080 00054 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000afd19b60 000F4 (v04 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xAFD4BF40/0x00000000AFD4BF80, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110413/tbfadt-560)
[    0.000000] ACPI: DSDT 00000000afd0d168 0C9F3 (v02 _ASUS_ Notebook 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000afd4bf40 00040
[    0.000000] ACPI: APIC 00000000afd19c58 00072 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: ECDT 00000000afd19cd0 000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000003)
[    0.000000] ACPI: MCFG 00000000afd19d98 0003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000afd19dd8 007AD (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: HPET 00000000afd1a588 00038 (v01 _ASUS_ Notebook 01072009 AMI  00000003)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000150000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000150000000
[    0.000000]   NODE_DATA [000000014fffb000 - 000000014fffffff]
[    0.000000]  [ffffea0000000000-ffffea00049fffff] PMD -> [ffff88014b600000-ffff88014effffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00150000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000afcc3
[    0.000000]     0: 0x000afd44 -> 0x000afd45
[    0.000000]     0: 0x000afd8e -> 0x000aff00
[    0.000000]     0: 0x00100001 -> 0x00150000
[    0.000000] On node 0 totalpages: 1048003
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 702062 pages, LIFO batch:31
[    0.000000]   Normal zone: 4480 pages used for memmap
[    0.000000]   Normal zone: 323199 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000afcc3000 - 00000000afd0d000
[    0.000000] PM: Registered nosave memory: 00000000afd0d000 - 00000000afd1b000
[    0.000000] PM: Registered nosave memory: 00000000afd1b000 - 00000000afd2c000
[    0.000000] PM: Registered nosave memory: 00000000afd2c000 - 00000000afd34000
[    0.000000] PM: Registered nosave memory: 00000000afd34000 - 00000000afd44000
[    0.000000] PM: Registered nosave memory: 00000000afd45000 - 00000000afd47000
[    0.000000] PM: Registered nosave memory: 00000000afd47000 - 00000000afd48000
[    0.000000] PM: Registered nosave memory: 00000000afd48000 - 00000000afd4b000
[    0.000000] PM: Registered nosave memory: 00000000afd4b000 - 00000000afd51000
[    0.000000] PM: Registered nosave memory: 00000000afd51000 - 00000000afd71000
[    0.000000] PM: Registered nosave memory: 00000000afd71000 - 00000000afd72000
[    0.000000] PM: Registered nosave memory: 00000000afd72000 - 00000000afd87000
[    0.000000] PM: Registered nosave memory: 00000000afd87000 - 00000000afd8e000
[    0.000000] PM: Registered nosave memory: 00000000aff00000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed01000
[    0.000000] PM: Registered nosave memory: 00000000fed01000 - 00000000fed61000
[    0.000000] PM: Registered nosave memory: 00000000fed61000 - 00000000fed71000
[    0.000000] PM: Registered nosave memory: 00000000fed71000 - 00000000fed80000
[    0.000000] PM: Registered nosave memory: 00000000fed80000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000ff800000
[    0.000000] PM: Registered nosave memory: 00000000ff800000 - 0000000100000000
[    0.000000] PM: Registered nosave memory: 0000000100000000 - 0000000100001000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:4ed00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88014fc00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029182
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=a1e12e24-2fc2-4e92-86a3-7a655eb37ab6 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ a4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ a4000000
[    0.000000] PM: Registered nosave memory: 00000000a4000000 - 00000000a8000000
[    0.000000] Memory: 3973636k/5505024k available (6109k kernel code, 1313012k absent, 218376k reserved, 4876k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2094.812 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4189.62 BogoMIPS (lpj=8379248)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004035] Security Framework initialized
[    0.004048] AppArmor: AppArmor initialized
[    0.004050] Yama: becoming mindful.
[    0.004503] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.005804] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.008518] Mount-cache hash table entries: 256
[    0.008646] Initializing cgroup subsys cpuacct
[    0.008651] Initializing cgroup subsys memory
[    0.008660] Initializing cgroup subsys devices
[    0.008662] Initializing cgroup subsys freezer
[    0.008664] Initializing cgroup subsys net_cls
[    0.008666] Initializing cgroup subsys blkio
[    0.008673] Initializing cgroup subsys perf_event
[    0.008699] tseg: 00aff00000
[    0.008701] CPU: Physical Processor ID: 0
[    0.008702] CPU: Processor Core ID: 0
[    0.008705] mce: CPU supports 6 MCE banks
[    0.008714] using AMD E400 aware idle routine
[    0.010209] ACPI: Core revision 20110413
[    0.020020] ftrace: allocating 25647 entries in 101 pages
[    0.024371] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.064344] CPU0: AMD Phenom(tm) II N830 Triple-Core Processor stepping 03
[    0.068003] Performance Events: AMD PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              48
[    0.068003] ... generic registers:      4
[    0.068003] ... value mask:             0000ffffffffffff
[    0.068003] ... max period:             00007fffffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000000000f
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 99000
[    0.156022] System has AMD C1E enabled
[    0.156034] Switch to broadcast mode on CPU1
[    0.156085]  #2
[    0.156087] smpboot cpu 2: start_ip = 99000
[    0.248027] Brought up 3 CPUs
[    0.248030] Total of 3 processors activated (12568.66 BogoMIPS).
[    0.248029] Switch to broadcast mode on CPU2
[    0.248515] Switch to broadcast mode on CPU0
[    0.248515] devtmpfs: initialized
[    0.248515] PM: Registering ACPI NVS region at afcc3000 (303104 bytes)
[    0.248515] PM: Registering ACPI NVS region at afd2c000 (32768 bytes)
[    0.248515] PM: Registering ACPI NVS region at afd47000 (4096 bytes)
[    0.248515] PM: Registering ACPI NVS region at afd4b000 (24576 bytes)
[    0.248515] PM: Registering ACPI NVS region at afd71000 (4096 bytes)
[    0.248515] PM: Registering ACPI NVS region at afd87000 (28672 bytes)
[    0.249532] print_constraints: dummy: 
[    0.249554] Time:  1:11:22  Date: 12/11/11
[    0.249591] NET: Registered protocol family 16
[    0.249702] node 0 link 0: io port [d000, ffff]
[    0.249706] TOM: 00000000b0000000 aka 2816M
[    0.249708] Fam 10h mmconf [e0000000, efffffff]
[    0.249711] node 0 link 0: mmio [a0000, bffff]
[    0.249713] node 0 link 0: mmio [b0000000, dfffffff]
[    0.249716] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.249719] node 0 link 0: mmio [f0000000, ff7fffff]
[    0.249721] TOM2: 0000000150000000 aka 5376M
[    0.249724] bus: [00, ff] on node 0 link 0
[    0.249727] bus: 00 index 0 [io  0x0000-0xffff]
[    0.249729] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.249731] bus: 00 index 2 [mem 0xb0000000-0xdfffffff]
[    0.249733] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.249735] bus: 00 index 4 [mem 0x150000000-0xfcffffffff]
[    0.249737] bus: [00, 06] on node 0 link 0
[    0.249746] Extended Config Space enabled on 1 nodes
[    0.249766] ACPI: bus type pci registered
[    0.249601] Trying to unpack rootfs image as initramfs...
[    0.249821] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.249825] PCI: not using MMCONFIG
[    0.249827] PCI: Using configuration type 1 for base access
[    0.249829] PCI: Using configuration type 1 for extended access
[    0.250469] bio: create slab <bio-0> at 0
[    0.250469] ACPI: EC: EC description table is found, configuring boot EC
[    0.250469] ACPI: EC: Look up EC in DSDT
[    0.251288] ACPI: Executed 2 blocks of module-level executable AML code
[    0.253901] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.284351] ACPI: Interpreter enabled
[    0.284357] ACPI: (supports S0 S3 S4 S5)
[    0.284379] ACPI: Using IOAPIC for interrupt routing
[    0.284552] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.284593] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.332721] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.332972] ACPI: No dock devices found.
[    0.332974] HEST: Table not found.
[    0.332978] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.333155] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.333295] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.333298] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.333301] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.333303] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000fffff]
[    0.333306] pci_root PNP0A03:00: host bridge window [mem 0xb0000000-0xffffffff]
[    0.333322] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    0.333368] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
[    0.333395] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.333398] pci 0000:00:02.0: PME# disabled
[    0.333416] pci 0000:00:04.0: [1022:9604] type 1 class 0x000604
[    0.333443] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.333445] pci 0000:00:04.0: PME# disabled
[    0.333459] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
[    0.333485] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.333487] pci 0000:00:05.0: PME# disabled
[    0.333524] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.333545] pci 0000:00:11.0: reg 10: [io  0xf090-0xf097]
[    0.333554] pci 0000:00:11.0: reg 14: [io  0xf080-0xf083]
[    0.333563] pci 0000:00:11.0: reg 18: [io  0xf070-0xf077]
[    0.333573] pci 0000:00:11.0: reg 1c: [io  0xf060-0xf063]
[    0.333582] pci 0000:00:11.0: reg 20: [io  0xf050-0xf05f]
[    0.333591] pci 0000:00:11.0: reg 24: [mem 0xfeb0a000-0xfeb0a3ff]
[    0.333644] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.333657] pci 0000:00:12.0: reg 10: [mem 0xfeb09000-0xfeb09fff]
[    0.333722] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.333740] pci 0000:00:12.2: reg 10: [mem 0xfeb08000-0xfeb080ff]
[    0.333805] pci 0000:00:12.2: supports D1 D2
[    0.333807] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.333811] pci 0000:00:12.2: PME# disabled
[    0.333831] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.333844] pci 0000:00:13.0: reg 10: [mem 0xfeb07000-0xfeb07fff]
[    0.333912] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.333930] pci 0000:00:13.2: reg 10: [mem 0xfeb06000-0xfeb060ff]
[    0.333995] pci 0000:00:13.2: supports D1 D2
[    0.333997] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.334001] pci 0000:00:13.2: PME# disabled
[    0.334021] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.334093] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.334113] pci 0000:00:14.2: reg 10: [mem 0xfeb00000-0xfeb03fff 64bit]
[    0.334167] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.334171] pci 0000:00:14.2: PME# disabled
[    0.334184] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.334254] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.334300] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    0.334313] pci 0000:00:16.0: reg 10: [mem 0xfeb05000-0xfeb05fff]
[    0.334378] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.334396] pci 0000:00:16.2: reg 10: [mem 0xfeb04000-0xfeb040ff]
[    0.334461] pci 0000:00:16.2: supports D1 D2
[    0.334463] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.334467] pci 0000:00:16.2: PME# disabled
[    0.334485] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.334503] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.334517] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.334531] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.334547] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.334601] pci 0000:01:00.0: [1002:68e0] type 0 class 0x000300
[    0.334614] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.334625] pci 0000:01:00.0: reg 18: [mem 0xfdf20000-0xfdf3ffff 64bit]
[    0.334632] pci 0000:01:00.0: reg 20: [io  0xe000-0xe0ff]
[    0.334645] pci 0000:01:00.0: reg 30: [mem 0xfdf00000-0xfdf1ffff pref]
[    0.334662] pci 0000:01:00.0: supports D1 D2
[    0.334680] pci 0000:01:00.1: [1002:aa68] type 0 class 0x000403
[    0.334693] pci 0000:01:00.1: reg 10: [mem 0xfdf40000-0xfdf43fff 64bit]
[    0.334735] pci 0000:01:00.1: supports D1 D2
[    0.344056] pci 0000:00:02.0: PCI bridge to [bus 01-03]
[    0.344063] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.344066] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfe8fffff]
[    0.344071] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.344114] pci 0000:04:00.0: [168c:002b] type 0 class 0x000280
[    0.344133] pci 0000:04:00.0: reg 10: [mem 0xfea00000-0xfea0ffff 64bit]
[    0.344197] pci 0000:04:00.0: supports D1
[    0.344199] pci 0000:04:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.344204] pci 0000:04:00.0: PME# disabled
[    0.352051] pci 0000:00:04.0: PCI bridge to [bus 04-04]
[    0.352057] pci 0000:00:04.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.352061] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.352066] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.352109] pci 0000:05:00.0: [197b:2382] type 0 class 0x000880
[    0.352126] pci 0000:05:00.0: reg 10: [mem 0xfe907000-0xfe9070ff]
[    0.352246] pci 0000:05:00.2: [197b:2381] type 0 class 0x000805
[    0.352262] pci 0000:05:00.2: reg 10: [mem 0xfe906000-0xfe9060ff]
[    0.352369] pci 0000:05:00.3: [197b:2383] type 0 class 0x000880
[    0.352384] pci 0000:05:00.3: reg 10: [mem 0xfe905000-0xfe9050ff]
[    0.352491] pci 0000:05:00.4: [197b:2384] type 0 class 0x000880
[    0.352506] pci 0000:05:00.4: reg 10: [mem 0xfe904000-0xfe9040ff]
[    0.352613] pci 0000:05:00.5: [197b:0250] type 0 class 0x000200
[    0.352629] pci 0000:05:00.5: reg 10: [mem 0xfe900000-0xfe903fff]
[    0.352649] pci 0000:05:00.5: reg 18: [io  0xd100-0xd17f]
[    0.352660] pci 0000:05:00.5: reg 1c: [io  0xd000-0xd0ff]
[    0.352718] pci 0000:05:00.5: PME# supported from D0 D3hot D3cold
[    0.352723] pci 0000:05:00.5: PME# disabled
[    0.360059] pci 0000:00:05.0: PCI bridge to [bus 05-05]
[    0.360066] pci 0000:00:05.0:   bridge window [io  0xd000-0xdfff]
[    0.360069] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.360073] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.360141] pci 0000:00:14.4: PCI bridge to [bus 06-06] (subtractive decode)
[    0.360145] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.360150] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.360155] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.360158] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.360161] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.360163] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.360166] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000fffff] (subtractive decode)
[    0.360169] pci 0000:00:14.4:   bridge window [mem 0xb0000000-0xffffffff] (subtractive decode)
[    0.360187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.360372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.360426] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.360458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.360593]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.360683]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x00
[    0.360685] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.361151] ACPI: PCI Interrupt Link [LN24] (IRQs *24)
[    0.361183] ACPI: PCI Interrupt Link [LN25] (IRQs *25)
[    0.361213] ACPI: PCI Interrupt Link [LN26] (IRQs *26)
[    0.361242] ACPI: PCI Interrupt Link [LN27] (IRQs *27)
[    0.361272] ACPI: PCI Interrupt Link [LN28] (IRQs *28)
[    0.361301] ACPI: PCI Interrupt Link [LN29] (IRQs *29)
[    0.361331] ACPI: PCI Interrupt Link [LN30] (IRQs *30)
[    0.361361] ACPI: PCI Interrupt Link [LN31] (IRQs *31)
[    0.361390] ACPI: PCI Interrupt Link [LN32] (IRQs *32)
[    0.361420] ACPI: PCI Interrupt Link [LN33] (IRQs *33)
[    0.361450] ACPI: PCI Interrupt Link [LN34] (IRQs *34)
[    0.361479] ACPI: PCI Interrupt Link [LN35] (IRQs *35)
[    0.361509] ACPI: PCI Interrupt Link [LN36] (IRQs *36)
[    0.361539] ACPI: PCI Interrupt Link [LN37] (IRQs *37)
[    0.361569] ACPI: PCI Interrupt Link [LN38] (IRQs *38)
[    0.361599] ACPI: PCI Interrupt Link [LN39] (IRQs *39)
[    0.361629] ACPI: PCI Interrupt Link [LN40] (IRQs *40)
[    0.361658] ACPI: PCI Interrupt Link [LN41] (IRQs *41)
[    0.361689] ACPI: PCI Interrupt Link [LN42] (IRQs *42)
[    0.361721] ACPI: PCI Interrupt Link [LN43] (IRQs *43)
[    0.361751] ACPI: PCI Interrupt Link [LN44] (IRQs *44)
[    0.361781] ACPI: PCI Interrupt Link [LN45] (IRQs *45)
[    0.361811] ACPI: PCI Interrupt Link [LN46] (IRQs *46)
[    0.361842] ACPI: PCI Interrupt Link [LN47] (IRQs *47)
[    0.361872] ACPI: PCI Interrupt Link [LN48] (IRQs *48)
[    0.361902] ACPI: PCI Interrupt Link [LN49] (IRQs *49)
[    0.361932] ACPI: PCI Interrupt Link [LN50] (IRQs *50)
[    0.361962] ACPI: PCI Interrupt Link [LN51] (IRQs *51)
[    0.361993] ACPI: PCI Interrupt Link [LN52] (IRQs *52)
[    0.362023] ACPI: PCI Interrupt Link [LN53] (IRQs *53)
[    0.362056] ACPI: PCI Interrupt Link [LN54] (IRQs *54)
[    0.362087] ACPI: PCI Interrupt Link [LN55] (IRQs *55)
[    0.362124] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
[    0.362185] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
[    0.362247] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
[    0.362309] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 14 15) *0
[    0.362357] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
[    0.362394] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
[    0.362431] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
[    0.362468] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
[    0.362581] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.362586] vgaarb: loaded
[    0.362588] vgaarb: bridge control possible 0000:01:00.0
[    0.362772] SCSI subsystem initialized
[    0.364074] libata version 3.00 loaded.
[    0.364117] usbcore: registered new interface driver usbfs
[    0.364128] usbcore: registered new interface driver hub
[    0.364139] usbcore: registered new device driver usb
[    0.364139] PCI: Using ACPI for IRQ routing
[    0.371008] PCI: pci_cache_line_size set to 64 bytes
[    0.371099] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.371101] reserve RAM buffer: 00000000afcc3000 - 00000000afffffff 
[    0.371106] reserve RAM buffer: 00000000afd45000 - 00000000afffffff 
[    0.371109] reserve RAM buffer: 00000000aff00000 - 00000000afffffff 
[    0.371208] NetLabel: Initializing
[    0.371209] NetLabel:  domain hash size = 128
[    0.371211] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.371221] NetLabel:  unlabeled traffic allowed by default
[    0.371294] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.371298] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.377057] Switching to clocksource hpet
[    0.378549] Switched to NOHz mode on CPU #2
[    0.378552] Switched to NOHz mode on CPU #1
[    0.378559] Switched to NOHz mode on CPU #0
[    0.381769] AppArmor: AppArmor Filesystem Enabled
[    0.381798] pnp: PnP ACPI init
[    0.381814] ACPI: bus type pnp registered
[    0.381929] pnp 00:00: [bus 00-ff]
[    0.381932] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.381934] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.381937] pnp 00:00: [io  0x0d00-0xffff window]
[    0.381939] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.381941] pnp 00:00: [mem 0x000c0000-0x000fffff window]
[    0.381944] pnp 00:00: [mem 0xb0000000-0xffffffff window]
[    0.382029] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.382070] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.382120] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.382123] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.382574] pnp 00:02: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.382577] pnp 00:02: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.382616] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.440184] pnp 00:03: [io  0x0010-0x001f]
[    0.440188] pnp 00:03: [io  0x0022-0x003f]
[    0.440191] pnp 00:03: [io  0x0062-0x0063]
[    0.440193] pnp 00:03: [io  0x0065-0x006f]
[    0.440194] pnp 00:03: [io  0x0072-0x007f]
[    0.440202] pnp 00:03: [io  0x0080]
[    0.440204] pnp 00:03: [io  0x0084-0x0086]
[    0.440206] pnp 00:03: [io  0x0088]
[    0.440207] pnp 00:03: [io  0x008c-0x008e]
[    0.440209] pnp 00:03: [io  0x0090-0x009f]
[    0.440211] pnp 00:03: [io  0x00a2-0x00bf]
[    0.440213] pnp 00:03: [io  0x00b1]
[    0.440214] pnp 00:03: [io  0x00e0-0x00ef]
[    0.440216] pnp 00:03: [io  0x04d0-0x04d1]
[    0.440218] pnp 00:03: [io  0x040b]
[    0.440220] pnp 00:03: [io  0x04d6]
[    0.440221] pnp 00:03: [io  0x0c00-0x0c01]
[    0.440223] pnp 00:03: [io  0x0c14]
[    0.440225] pnp 00:03: [io  0x0c50-0x0c51]
[    0.440226] pnp 00:03: [io  0x0c52]
[    0.440228] pnp 00:03: [io  0x0c6c]
[    0.440230] pnp 00:03: [io  0x0c6f]
[    0.440231] pnp 00:03: [io  0x0cd0-0x0cd1]
[    0.440233] pnp 00:03: [io  0x0cd2-0x0cd3]
[    0.440235] pnp 00:03: [io  0x0cd4-0x0cd5]
[    0.440236] pnp 00:03: [io  0x0cd6-0x0cd7]
[    0.440238] pnp 00:03: [io  0x0cd8-0x0cdf]
[    0.440240] pnp 00:03: [io  0x0800-0x089f]
[    0.440242] pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
[    0.440244] pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
[    0.440247] pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
[    0.440249] pnp 00:03: [io  0x0900-0x090f]
[    0.440250] pnp 00:03: [io  0x0910-0x091f]
[    0.440252] pnp 00:03: [io  0xfe00-0xfefe]
[    0.440254] pnp 00:03: [io  0x0060-0x005f disabled]
[    0.440256] pnp 00:03: [io  0x0064-0x0063 disabled]
[    0.440259] pnp 00:03: [mem 0xfec00000-0xfec00fff]
[    0.440261] pnp 00:03: [mem 0xfee00000-0xfee00fff]
[    0.440263] pnp 00:03: [mem 0xfed80000-0xfed8ffff]
[    0.440265] pnp 00:03: [mem 0xfed61000-0xfed70fff]
[    0.440266] pnp 00:03: [mem 0xfec10000-0xfec10fff]
[    0.440268] pnp 00:03: [mem 0xfed00000-0xfed00fff]
[    0.440270] pnp 00:03: [mem 0xff800000-0xffffffff]
[    0.440381] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.440384] system 00:03: [io  0x040b] has been reserved
[    0.440386] system 00:03: [io  0x04d6] has been reserved
[    0.440389] system 00:03: [io  0x0c00-0x0c01] has been reserved
[    0.440391] system 00:03: [io  0x0c14] has been reserved
[    0.440394] system 00:03: [io  0x0c50-0x0c51] has been reserved
[    0.440396] system 00:03: [io  0x0c52] has been reserved
[    0.440398] system 00:03: [io  0x0c6c] has been reserved
[    0.440401] system 00:03: [io  0x0c6f] has been reserved
[    0.440403] system 00:03: [io  0x0cd0-0x0cd1] has been reserved
[    0.440405] system 00:03: [io  0x0cd2-0x0cd3] has been reserved
[    0.440408] system 00:03: [io  0x0cd4-0x0cd5] has been reserved
[    0.440410] system 00:03: [io  0x0cd6-0x0cd7] has been reserved
[    0.440413] system 00:03: [io  0x0cd8-0x0cdf] has been reserved
[    0.440415] system 00:03: [io  0x0800-0x089f] has been reserved
[    0.440418] system 00:03: [io  0x0900-0x090f] has been reserved
[    0.440420] system 00:03: [io  0x0910-0x091f] has been reserved
[    0.440423] system 00:03: [io  0xfe00-0xfefe] has been reserved
[    0.440427] system 00:03: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.440430] system 00:03: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.440432] system 00:03: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.440435] system 00:03: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.440438] system 00:03: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.440441] system 00:03: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.440444] system 00:03: [mem 0xff800000-0xffffffff] has been reserved
[    0.440448] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.440463] pnp 00:04: [dma 4]
[    0.440465] pnp 00:04: [io  0x0000-0x000f]
[    0.440467] pnp 00:04: [io  0x0081-0x0083]
[    0.440469] pnp 00:04: [io  0x0087]
[    0.440472] pnp 00:04: [io  0x0089-0x008b]
[    0.440474] pnp 00:04: [io  0x008f]
[    0.440476] pnp 00:04: [io  0x00c0-0x00df]
[    0.440498] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.440508] pnp 00:05: [io  0x0070-0x0071]
[    0.440517] pnp 00:05: [irq 8]
[    0.440540] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.440548] pnp 00:06: [io  0x0061]
[    0.440568] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.440585] pnp 00:07: [io  0x0010-0x001f]
[    0.440587] pnp 00:07: [io  0x0022-0x003f]
[    0.440588] pnp 00:07: [io  0x0044-0x005f]
[    0.440590] pnp 00:07: [io  0x0062-0x0063]
[    0.440592] pnp 00:07: [io  0x0065-0x006f]
[    0.440594] pnp 00:07: [io  0x0072-0x007f]
[    0.440596] pnp 00:07: [io  0x0080]
[    0.440598] pnp 00:07: [io  0x0084-0x0086]
[    0.440599] pnp 00:07: [io  0x0088]
[    0.440601] pnp 00:07: [io  0x008c-0x008e]
[    0.440603] pnp 00:07: [io  0x0090-0x009f]
[    0.440605] pnp 00:07: [io  0x00a2-0x00bf]
[    0.440607] pnp 00:07: [io  0x00e0-0x00ef]
[    0.440608] pnp 00:07: [io  0x04d0-0x04d1]
[    0.440653] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.440656] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.440664] pnp 00:08: [io  0x00f0-0x00ff]
[    0.440672] pnp 00:08: [irq 13]
[    0.440693] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.440740] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.440752] pnp 00:0a: [io  0x0240-0x0259]
[    0.440796] system 00:0a: [io  0x0240-0x0259] has been reserved
[    0.440799] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.440847] pnp 00:0b: [irq 12]
[    0.440873] pnp 00:0b: Plug and Play ACPI device, IDs ETD0001 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.440894] pnp 00:0c: [io  0x0060]
[    0.440896] pnp 00:0c: [io  0x0064]
[    0.440900] pnp 00:0c: [irq 1]
[    0.440924] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.441302] pnp 00:0d: [mem 0xfed00000-0xfed003ff]
[    0.441357] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.441363] pnp: PnP ACPI: found 14 devices
[    0.441365] ACPI: ACPI bus type pnp unregistered
[    0.447217] PCI: max bus depth: 1 pci_try_num: 2
[    0.447242] pci 0000:00:02.0: PCI bridge to [bus 01-03]
[    0.447245] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.447248] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfe8fffff]
[    0.447252] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.447256] pci 0000:00:04.0: PCI bridge to [bus 04-04]
[    0.447258] pci 0000:00:04.0:   bridge window [io  disabled]
[    0.447261] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.447264] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    0.447268] pci 0000:00:05.0: PCI bridge to [bus 05-05]
[    0.447270] pci 0000:00:05.0:   bridge window [io  0xd000-0xdfff]
[    0.447274] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.447276] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.447280] pci 0000:00:14.4: PCI bridge to [bus 06-06]
[    0.447282] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.447287] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.447291] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.447312] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.447317] pci 0000:00:02.0: setting latency timer to 64
[    0.447326] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.447329] pci 0000:00:04.0: setting latency timer to 64
[    0.447336] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.447339] pci 0000:00:05.0: setting latency timer to 64
[    0.447347] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.447350] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.447352] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.447355] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000fffff]
[    0.447357] pci_bus 0000:00: resource 8 [mem 0xb0000000-0xffffffff]
[    0.447360] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.447362] pci_bus 0000:01: resource 1 [mem 0xfdf00000-0xfe8fffff]
[    0.447364] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.447367] pci_bus 0000:04: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.447370] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
[    0.447372] pci_bus 0000:05: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.447374] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.447377] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.447379] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.447381] pci_bus 0000:06: resource 7 [mem 0x000c0000-0x000fffff]
[    0.447383] pci_bus 0000:06: resource 8 [mem 0xb0000000-0xffffffff]
[    0.447424] NET: Registered protocol family 2
[    0.447588] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.448885] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.451572] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.451894] TCP: Hash tables configured (established 524288 bind 65536)
[    0.451897] TCP reno registered
[    0.451910] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.451946] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.452104] NET: Registered protocol family 1
[    0.504235] pci 0000:01:00.0: Boot video device
[    0.504255] PCI: CLS 64 bytes, default 64
[    0.505633] PCI-DMA: Disabling AGP.
[    0.505711] PCI-DMA: aperture base @ a4000000 size 65536 KB
[    0.505713] PCI-DMA: using GART IOMMU.
[    0.505716] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.509383] audit: initializing netlink socket (disabled)
[    0.509397] type=2000 audit(1323565881.508:1): initialized
[    0.539134] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.557246] VFS: Disk quotas dquot_6.5.2
[    0.557312] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.558001] fuse init (API version 7.16)
[    0.558125] msgmni has been set to 7889
[    0.558710] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.558783] io scheduler noop registered
[    0.558787] io scheduler deadline registered
[    0.558864] io scheduler cfq registered (default)
[    0.559079] pcieport 0000:00:02.0: setting latency timer to 64
[    0.559113] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.559242] pcieport 0000:00:04.0: setting latency timer to 64
[    0.559267] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    0.559381] pcieport 0000:00:05.0: setting latency timer to 64
[    0.559404] pcieport 0000:00:05.0: irq 42 for MSI/MSI-X
[    0.559527] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.559559] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.559675] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.559724] ACPI: AC Adapter [AC0] (on-line)
[    0.559839] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.559844] ACPI: Power Button [PWRB]
[    0.559882] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.561441] ACPI: Lid Switch [LID]
[    0.561500] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.561506] ACPI: Sleep Button [SLPB]
[    0.561545] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.561548] ACPI: Power Button [PWRF]
[    0.561599] ACPI: acpi_idle registered with cpuidle
[    0.561656] ACPI: processor limited to max C-state 1
[    0.569906] ACPI Warning: For \_TZ_.THRM._PSL: Return Package has no elements (empty) (20110413/nspredef-457)
[    0.569915] ACPI: [Package] has zero elements (ffff880148fb50c0)
[    0.569917] ACPI: Invalid passive threshold
[    0.570358] thermal LNXTHERM:00: registered as thermal_zone0
[    0.570363] ACPI: Thermal Zone [THRM] (64 C)
[    0.570412] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.570446] ERST: Table is not found!
[    0.570532] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.583514] Freeing initrd memory: 13440k freed
[    0.609982] ACPI: Battery Slot [BAT0] (battery present)
[    0.696609] Linux agpgart interface v0.103
[    0.697543] brd: module loaded
[    0.697969] loop: module loaded
[    0.698374] Fixed MDIO Bus: probed
[    0.698394] PPP generic driver version 2.4.2
[    0.698434] tun: Universal TUN/TAP device driver, 1.6
[    0.698436] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.698505] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.698696] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.698743] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.698811] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.698824] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.698842] QUIRK: Enable AMD PLL fix
[    0.698853] ehci_hcd 0000:00:12.2: debug port 1
[    0.698876] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfeb08000
[    0.708113] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.708254] hub 1-0:1.0: USB hub found
[    0.708258] hub 1-0:1.0: 5 ports detected
[    0.708426] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.708448] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.708491] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.708500] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.708521] ehci_hcd 0000:00:13.2: debug port 1
[    0.708535] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfeb06000
[    0.720111] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.720254] hub 2-0:1.0: USB hub found
[    0.720258] hub 2-0:1.0: 5 ports detected
[    0.720426] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.720448] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    0.720488] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    0.720497] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.720518] ehci_hcd 0000:00:16.2: debug port 1
[    0.720533] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfeb04000
[    0.732111] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    0.732253] hub 3-0:1.0: USB hub found
[    0.732257] hub 3-0:1.0: 4 ports detected
[    0.732384] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732471] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.732495] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.732544] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    0.732579] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfeb09000
[    0.792232] hub 4-0:1.0: USB hub found
[    0.792245] hub 4-0:1.0: 5 ports detected
[    0.792403] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.792426] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.792464] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.792485] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfeb07000
[    0.852240] hub 5-0:1.0: USB hub found
[    0.852251] hub 5-0:1.0: 5 ports detected
[    0.852443] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.852467] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    0.852508] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 6
[    0.852528] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfeb05000
[    0.912251] hub 6-0:1.0: USB hub found
[    0.912262] hub 6-0:1.0: 4 ports detected
[    0.912378] uhci_hcd: USB Universal Host Controller Interface driver
[    0.912463] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.916757] i8042: Detected active multiplexing controller, rev 1.1
[    0.918202] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.918209] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.918240] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.918259] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.918279] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.918394] mousedev: PS/2 mouse device common for all mice
[    0.918567] rtc_cmos 00:05: RTC can wake from S4
[    0.918653] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.918675] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.918771] device-mapper: uevent: version 1.0.3
[    0.918833] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    0.918844] cpuidle: using governor ladder
[    0.918846] cpuidle: using governor menu
[    0.918848] EFI Variables Facility v0.08 2004-May-17
[    0.919068] TCP cubic registered
[    0.919176] NET: Registered protocol family 10
[    0.919639] NET: Registered protocol family 17
[    0.919658] Registering the dns_resolver key type
[    0.919750] PM: Hibernation image not present or could not be loaded.
[    0.919761] registered taskstats version 1
[    0.935518]   Magic number: 7:581:154
[    0.935537] bdi 1:6: hash matches
[    0.935581] acpi device:21: hash matches
[    0.935673] rtc_cmos 00:05: setting system clock to 2011-12-11 01:11:23 UTC (1323565883)
[    0.935687] powernow-k8: Found 1 AMD Phenom(tm) II N830 Triple-Core Processor (3 cpu cores) (version 2.20.00)
[    0.935725] powernow-k8:    0 : pstate 0 (2100 MHz)
[    0.935727] powernow-k8:    1 : pstate 1 (1800 MHz)
[    0.935728] powernow-k8:    2 : pstate 2 (1500 MHz)
[    0.935730] powernow-k8:    3 : pstate 3 (1200 MHz)
[    0.935732] powernow-k8:    4 : pstate 4 (800 MHz)
[    0.936055] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.936058] EDD information not available.
[    0.937841] Freeing unused kernel memory: 984k freed
[    0.938100] Write protecting the kernel read-only data: 10240k
[    0.938355] Freeing unused kernel memory: 16k freed
[    0.943652] Freeing unused kernel memory: 1396k freed
[    0.957009] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.967534] udevd[122]: starting version 173
[    1.026897] sdhci: Secure Digital Host Controller Interface driver
[    1.026900] sdhci: Copyright(c) Pierre Ossman
[    1.038901] sdhci-pci 0000:05:00.0: SDHCI controller found [197b:2382] (rev 80)
[    1.038921] sdhci-pci 0000:05:00.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.038971] sdhci-pci 0000:05:00.0: setting latency timer to 64
[    1.038984] mmc0: no vmmc regulator found
[    1.039023] Registered led device: mmc0::
[    1.039057] mmc0: SDHCI controller on PCI [0000:05:00.0] using ADMA
[    1.041324] sdhci-pci 0000:05:00.2: SDHCI controller found [197b:2381] (rev 80)
[    1.041342] sdhci-pci 0000:05:00.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.041353] sdhci-pci 0000:05:00.2: Refusing to bind to secondary interface.
[    1.041359] sdhci-pci 0000:05:00.2: PCI INT B disabled
[    1.043025] jme: JMicron JMC2XX ethernet driver version 1.0.8
[    1.044109] jme 0000:05:00.5: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.044122] jme 0000:05:00.5: setting latency timer to 64
[    1.045202] jme 0000:05:00.5: eth0: JMC250 Gigabit Ethernet chiprev:23 pcirev:3 macaddr:bc:ae:c5:64:7f:ab
[    1.045234] ahci 0000:00:11.0: version 3.0
[    1.045256] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.045308] ahci 0000:00:11.0: irq 43 for MSI/MSI-X
[    1.045394] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.045398] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.046799] scsi0 : ahci
[    1.048037] scsi1 : ahci
[    1.051213] scsi2 : ahci
[    1.053135] scsi3 : ahci
[    1.053210] ata1: SATA max UDMA/133 abar m1024@0xfeb0a000 port 0xfeb0a100 irq 43
[    1.053214] ata2: SATA max UDMA/133 abar m1024@0xfeb0a000 port 0xfeb0a180 irq 43
[    1.053218] ata3: SATA max UDMA/133 abar m1024@0xfeb0a000 port 0xfeb0a200 irq 43
[    1.053221] ata4: SATA max UDMA/133 abar m1024@0xfeb0a000 port 0xfeb0a280 irq 43
[    1.192124] usb 2-2: new high speed USB device number 2 using ehci_hcd
[    1.376145] ata4: SATA link down (SStatus 0 SControl 300)
[    1.380129] ata3: SATA link down (SStatus 0 SControl 300)
[    1.508088] Refined TSC clocksource calibration: 2094.754 MHz.
[    1.508100] Switching to clocksource tsc
[    1.544115] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.550398] ata1.00: ATA-8: SAMSUNG HN-M101MBB, 2AR10001, max UDMA/133
[    1.550402] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.556714] ata1.00: configured for UDMA/133
[    1.556930] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HN-M101M 2AR1 PQ: 0 ANSI: 5
[    1.557116] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.557127] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.557170] sd 0:0:0:0: [sda] Write Protect is off
[    1.557174] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.557190] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.560118] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.562719] ata2.00: ATAPI: HL-DT-STDVDRAM GT34N, AS00, max UDMA/100
[    1.565773] ata2.00: configured for UDMA/100
[    1.568816] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT34N     AS00 PQ: 0 ANSI: 5
[    1.573036] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.573041] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.573178] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.573248] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.619163]  sda: sda1 sda2 sda3 < sda5 >
[    1.619501] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.624127] usb 4-1: new full speed USB device number 2 using ohci_hcd
[    2.052065] usb 4-2: new low speed USB device number 3 using ohci_hcd
[    2.142420] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.740824] udevd[392]: starting version 173
[    5.243369] Adding 1998844k swap on /dev/sda5.  Priority:-1 extents:1 across:1998844k 
[    6.171543] lp: driver loaded but no devices found
[    6.356712] asus_laptop: Asus Laptop Support version 0.42
[    6.356896] asus_laptop: BSTS called, 0xfd7f returned
[    6.430860] asus_laptop: Backlight controlled by ACPI video driver
[    6.430935] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input5
[    6.434437] ACPI Warning: _BQC returned an invalid level (20110413/video-473)
[    6.436870] acpi device:40: registered as cooling_device3
[    6.437109] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:3d/LNXVIDEO:00/input/input6
[    6.437170] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    6.646867] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    6.705435] [drm] Initialized drm 1.1.0 20060810
[    6.909719] jmb38x_ms 0000:05:00.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    6.909727] jmb38x_ms 0000:05:00.3: setting latency timer to 64
[    6.913973] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    6.914075] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[    6.989330] elantech: assuming hardware version 2, firmware version 4.1.2
[    7.024145] elantech: Synaptics capabilities query result 0x78, 0x16, 0x0d.
[    7.074845] MCE: In-kernel MCE decoding enabled.
[    7.084437] cfg80211: Calling CRDA to update world regulatory domain
[    7.123421] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input7
[    7.233414] EDAC MC: Ver: 2.1.0
[    7.334788] AMD64 EDAC driver v3.4.0
[    7.335077] EDAC amd64: DRAM ECC disabled.
[    7.335097] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    7.335099]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    7.335100]  (Note that use of the override may cause unknown side effects.)
[    7.421829] Bluetooth: Core ver 2.16
[    7.421867] NET: Registered protocol family 31
[    7.421869] Bluetooth: HCI device and connection manager initialized
[    7.421872] Bluetooth: HCI socket layer initialized
[    7.421874] Bluetooth: L2CAP socket layer initialized
[    7.421946] Bluetooth: SCO socket layer initialized
[    8.148708] [drm] radeon defaulting to kernel modesetting.
[    8.148712] [drm] radeon kernel modesetting enabled.
[    8.148851] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.148858] radeon 0000:01:00.0: setting latency timer to 64
[    8.149091] [drm] initializing kernel modesetting (CEDAR 0x1002:0x68E0 0x1043:0x1BF2).
[    8.149134] [drm] register mmio base: 0xFDF20000
[    8.149136] [drm] register mmio size: 131072
[    8.149285] ATOM BIOS: Asus
[    8.149361] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    8.149364] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[    8.149577] [drm] Detected VRAM RAM=512M, BAR=256M
[    8.149581] [drm] RAM width 64bits DDR
[    8.149676] [TTM] Zone  kernel: Available graphics memory: 2027712 kiB.
[    8.149678] [TTM] Initializing pool allocator.
[    8.149704] [drm] radeon: 512M of VRAM memory ready
[    8.149706] [drm] radeon: 512M of GTT memory ready.
[    8.149726] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.149727] [drm] Driver supports precise vblank timestamp query.
[    8.149767] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[    8.149773] radeon 0000:01:00.0: radeon: using MSI.
[    8.149805] [drm] radeon: irq initialized.
[    8.149810] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    8.150788] [drm] Loading CEDAR Microcode
[    8.317732] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    8.317943] usbcore: registered new interface driver btusb
[    8.367959] ath9k 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.367971] ath9k 0000:04:00.0: setting latency timer to 64
[    8.416890] ath: EEPROM regdomain: 0x60
[    8.416892] ath: EEPROM indicates we should expect a direct regpair map
[    8.416896] ath: Country alpha2 being used: 00
[    8.416897] ath: Regpair used: 0x60
[    8.416900] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    8.416903] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416905] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    8.416908] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416910] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    8.416913] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416915] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    8.416918] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416920] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    8.416922] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416924] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    8.416927] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416929] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    8.416932] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416934] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    8.416937] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416939] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    8.416942] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416944] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    8.416947] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416949] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    8.416951] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416953] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    8.416956] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416958] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    8.416961] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.416963] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    8.416966] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.418743] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    8.483722] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    8.484312] Registered led device: ath9k-phy0
[    8.484321] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90011140000, irq=16
[    8.824335] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    8.824340] cfg80211: World regulatory domain updated:
[    8.824342] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.824345] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.824348] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.824350] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.824353] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.824355] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.424402] type=1400 audit(1323576691.986:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=653 comm="apparmor_parser"
[    9.424427] type=1400 audit(1323576691.986:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=743 comm="apparmor_parser"
[    9.424452] type=1400 audit(1323576691.986:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=548 comm="apparmor_parser"
[    9.424899] type=1400 audit(1323576691.986:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=653 comm="apparmor_parser"
[    9.424932] type=1400 audit(1323576691.986:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=743 comm="apparmor_parser"
[    9.424967] type=1400 audit(1323576691.986:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=548 comm="apparmor_parser"
[    9.425218] type=1400 audit(1323576691.986:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=653 comm="apparmor_parser"
[    9.425254] type=1400 audit(1323576691.986:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=743 comm="apparmor_parser"
[    9.425295] type=1400 audit(1323576691.986:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=548 comm="apparmor_parser"
[    9.558440] input: 2.4G Receiver as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input8
[    9.558539] generic-usb 0003:1D57:32DA.0001: input,hidraw0: USB HID v1.10 Keyboard [2.4G Receiver] on usb-0000:00:12.0-2/input0
[    9.563403] input: 2.4G Receiver as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input9
[    9.563532] generic-usb 0003:1D57:32DA.0002: input,hidraw1: USB HID v1.10 Mouse [2.4G Receiver] on usb-0000:00:12.0-2/input1
[    9.572381] input: 2.4G Receiver as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.2/input/input10
[    9.572496] generic-usb 0003:1D57:32DA.0003: input,hidraw2: USB HID v1.10 Device [2.4G Receiver] on usb-0000:00:12.0-2/input2
[    9.572514] usbcore: registered new interface driver usbhid
[    9.572516] usbhid: USB HID core driver
[    9.583594] Linux video capture interface: v2.00
[   10.052827] uvcvideo: Found UVC 1.00 device USB2.0 0.3M UVC

---

### Post by anforguiven on 2011-12-10
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

/var/log/dmesg (parte 2)

WebCam (04f2:b1e5)
[   10.063624] input: USB2.0 0.3M UVC WebCam as /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input11
[   10.063700] usbcore: registered new interface driver uvcvideo
[   10.063702] USB Video Class driver (v1.1.0)
[   10.074899] radeon 0000:01:00.0: WB enabled
[   10.091012] [drm] ring test succeeded in 1 usecs
[   10.091138] [drm] radeon: ib pool ready.
[   10.091203] [drm] ib test succeeded in 0 usecs
[   10.091510] [drm] Radeon Display Connectors
[   10.091512] [drm] Connector 0:
[   10.091513] [drm]   LVDS
[   10.091515] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[   10.091517] [drm]   Encoders:
[   10.091519] [drm]     LCD1: INTERNAL_UNIPHY
[   10.091520] [drm] Connector 1:
[   10.091521] [drm]   HDMI-A
[   10.091523] [drm]   HPD1
[   10.091525] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[   10.091526] [drm]   Encoders:
[   10.091528] [drm]     DFP1: INTERNAL_UNIPHY1
[   10.091529] [drm] Connector 2:
[   10.091530] [drm]   VGA
[   10.091532] [drm]   DDC: 0x64d8 0x64d8 0x64dc 0x64dc 0x64e0 0x64e0 0x64e4 0x64e4
[   10.091534] [drm]   Encoders:
[   10.091535] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   10.101717] [drm] Radeon display connector LVDS-1: No monitor connected or invalid EDID
[   10.111626] [drm] Radeon display connector HDMI-A-1: No monitor connected or invalid EDID
[   10.121522] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
[   10.121554] [drm] Internal thermal controller without fan control
[   10.121606] [drm] radeon: power management initialized
[   10.487724] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.548061] [drm] fb mappable at 0xD0141000
[   10.548069] [drm] vram apper at 0xD0000000
[   10.548071] [drm] size 4325376
[   10.548072] [drm] fb depth is 24
[   10.548074] [drm]    pitch is 5632
[   10.548166] fbcon: radeondrmfb (fb0) is primary device
[   10.548264] Console: switching to colour frame buffer device 170x48
[   10.548288] fb0: radeondrmfb frame buffer device
[   10.548290] drm: registered panic notifier
[   10.548298] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:00.0 on minor 0
[   10.685645] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   10.685726] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input13
[   10.685929] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   10.686012] HDA Intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   10.686038] HDA Intel 0000:01:00.1: setting latency timer to 64
[   10.842243] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   10.842370] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
[   13.425054] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.647835] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   14.809225] ppdev: user-space parallel port driver
[   14.976310] type=1400 audit(1323576697.538:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1076 comm="apparmor_parser"
[   14.976918] type=1400 audit(1323576697.538:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1076 comm="apparmor_parser"
[   15.407622] type=1400 audit(1323576697.966:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1095 comm="apparmor_parser"
[   15.408169] type=1400 audit(1323576697.970:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1095 comm="apparmor_parser"
[   15.408491] type=1400 audit(1323576697.970:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1095 comm="apparmor_parser"
[   15.617231] type=1400 audit(1323576698.178:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1094 comm="apparmor_parser"
[   16.077011] type=1400 audit(1323576698.638:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1102 comm="apparmor_parser"
[   16.077648] type=1400 audit(1323576698.638:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1102 comm="apparmor_parser"
[   16.168303] type=1400 audit(1323576698.730:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1103 comm="apparmor_parser"
[   16.174912] type=1400 audit(1323576698.734:20): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1098 comm="apparmor_parser"
[   17.102575] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.108331] jme 0000:05:00.5: irq 46 for MSI/MSI-X
[   17.108897] jme 0000:05:00.5: eth0: Link is down
[   17.109453] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.358725] init: failsafe main process (1023) killed by TERM signal
[   17.362058] init: apport pre-start process (1147) terminated with status 1
[   17.369773] init: apport post-stop process (1168) terminated with status 1

---

### Post by anforguiven on 2011-12-10
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

/var/log/Xorg.0.log

[    18.330] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    18.330] X Protocol Version 11, Revision 0
[    18.330] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    18.330] Current Operating System: Linux ASUS 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64
[    18.331] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=a1e12e24-2fc2-4e92-86a3-7a655eb37ab6 ro quiet splash vt.handoff=7
[    18.331] Build Date: 19 October 2011  05:21:26AM
[    18.331] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    18.331] Current version of pixman: 0.22.2
[    18.331] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    18.331] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.331] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 11 01:11:40 2011
[    18.443] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.571] (==) No Layout section.  Using the first Screen section.
[    18.571] (==) No screen section available. Using defaults.
[    18.571] (**) |-->Screen "Default Screen Section" (0)
[    18.571] (**) |   |-->Monitor "<default monitor>"
[    18.571] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    18.571] (==) Automatically adding devices
[    18.571] (==) Automatically enabling devices
[    18.597] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.597] 	Entry deleted from font path.
[    18.597] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.597] 	Entry deleted from font path.
[    18.597] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.597] 	Entry deleted from font path.
[    18.597] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.597] 	Entry deleted from font path.
[    18.597] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.597] 	Entry deleted from font path.
[    18.603] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    18.603] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.603] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.603] (II) Loader magic: 0x7e0220
[    18.603] (II) Module ABI versions:
[    18.603] 	X.Org ANSI C Emulation: 0.4
[    18.603] 	X.Org Video Driver: 10.0
[    18.603] 	X.Org XInput driver : 12.3
[    18.603] 	X.Org Server Extension : 5.0
[    18.604] (--) PCI:*(0:1:0:0) 1002:68e0:1043:1bf2 rev 0, Mem @ 0xd0000000/268435456, 0xfdf20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    18.604] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.604] (II) LoadModule: "extmod"
[    18.613] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.619] (II) Module extmod: vendor="X.Org Foundation"
[    18.619] 	compiled for 1.10.4, module version = 1.0.0
[    18.619] 	Module class: X.Org Server Extension
[    18.619] 	ABI class: X.Org Server Extension, version 5.0
[    18.619] (II) Loading extension MIT-SCREEN-SAVER
[    18.619] (II) Loading extension XFree86-VidModeExtension
[    18.619] (II) Loading extension XFree86-DGA
[    18.619] (II) Loading extension DPMS
[    18.619] (II) Loading extension XVideo
[    18.619] (II) Loading extension XVideo-MotionCompensation
[    18.619] (II) Loading extension X-Resource
[    18.619] (II) LoadModule: "dbe"
[    18.619] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.620] (II) Module dbe: vendor="X.Org Foundation"
[    18.620] 	compiled for 1.10.4, module version = 1.0.0
[    18.620] 	Module class: X.Org Server Extension
[    18.620] 	ABI class: X.Org Server Extension, version 5.0
[    18.620] (II) Loading extension DOUBLE-BUFFER
[    18.620] (II) LoadModule: "glx"
[    18.620] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.649] (II) Module glx: vendor="X.Org Foundation"
[    18.649] 	compiled for 1.10.4, module version = 1.0.0
[    18.649] 	ABI class: X.Org Server Extension, version 5.0
[    18.649] (==) AIGLX enabled
[    18.649] (II) Loading extension GLX
[    18.661] (II) LoadModule: "record"
[    18.661] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.684] (II) Module record: vendor="X.Org Foundation"
[    18.684] 	compiled for 1.10.4, module version = 1.13.0
[    18.684] 	Module class: X.Org Server Extension
[    18.684] 	ABI class: X.Org Server Extension, version 5.0
[    18.684] (II) Loading extension RECORD
[    18.684] (II) LoadModule: "dri"
[    18.684] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.698] (II) Module dri: vendor="X.Org Foundation"
[    18.698] 	compiled for 1.10.4, module version = 1.0.0
[    18.698] 	ABI class: X.Org Server Extension, version 5.0
[    18.698] (II) Loading extension XFree86-DRI
[    18.698] (II) LoadModule: "dri2"
[    18.698] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.720] (II) Module dri2: vendor="X.Org Foundation"
[    18.720] 	compiled for 1.10.4, module version = 1.2.0
[    18.720] 	ABI class: X.Org Server Extension, version 5.0
[    18.720] (II) Loading extension DRI2
[    18.720] (==) Matched fglrx as autoconfigured driver 0
[    18.720] (==) Matched ati as autoconfigured driver 1
[    18.720] (==) Matched vesa as autoconfigured driver 2
[    18.720] (==) Matched fbdev as autoconfigured driver 3
[    18.720] (==) Assigned the driver to the xf86ConfigLayout
[    18.720] (II) LoadModule: "fglrx"
[    18.728] (WW) Warning, couldn't open module fglrx
[    18.728] (II) UnloadModule: "fglrx"
[    18.728] (II) Unloading fglrx
[    18.728] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    18.728] (II) LoadModule: "ati"
[    18.728] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    18.739] (II) Module ati: vendor="X.Org Foundation"
[    18.739] 	compiled for 1.10.2.902, module version = 6.14.99
[    18.739] 	Module class: X.Org Video Driver
[    18.739] 	ABI class: X.Org Video Driver, version 10.0
[    18.739] (II) LoadModule: "radeon"
[    18.739] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    18.848] (II) Module radeon: vendor="X.Org Foundation"
[    18.848] 	compiled for 1.10.2.902, module version = 6.14.99
[    18.848] 	Module class: X.Org Video Driver
[    18.848] 	ABI class: X.Org Video Driver, version 10.0
[    18.858] (II) LoadModule: "vesa"
[    18.858] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.908] (II) Module vesa: vendor="X.Org Foundation"
[    18.908] 	compiled for 1.10.2, module version = 2.3.0
[    18.908] 	Module class: X.Org Video Driver
[    18.908] 	ABI class: X.Org Video Driver, version 10.0
[    18.909] (II) LoadModule: "fbdev"
[    18.909] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.962] (II) Module fbdev: vendor="X.Org Foundation"
[    18.962] 	compiled for 1.10.0, module version = 0.4.2
[    18.962] 	ABI class: X.Org Video Driver, version 10.0
[    18.962] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS
[    18.964] (II) VESA: driver for VESA chipsets: vesa
[    18.964] (II) FBDEV: driver for framebuffer: fbdev
[    18.964] (++) using VT number 7

[    18.964] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    18.964] (II) [KMS] Kernel modesetting enabled.
[    18.964] (WW) Falling back to old probe method for vesa
[    18.964] (WW) Falling back to old probe method for fbdev
[    18.964] (II) Loading sub module "fbdevhw"
[    18.964] (II) LoadModule: "fbdevhw"
[    18.965] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.979] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.979] 	compiled for 1.10.4, module version = 0.0.2
[    18.979] 	ABI class: X.Org Video Driver, version 10.0
[    18.983] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    18.983] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    18.983] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    18.983] (==) RADEON(0): Default visual is TrueColor
[    18.984] (==) RADEON(0): RGB weight 888
[    18.984] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    18.984] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 5000 Series" (ChipID = 0x68e0)
[    18.984] (II) RADEON(0): PCIE card detected
[    18.984] drmOpenDevice: node name is /dev/dri/card0
[    18.984] drmOpenDevice: open result is 12, (OK)
[    18.984] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    18.984] drmOpenDevice: node name is /dev/dri/card0
[    18.984] drmOpenDevice: open result is 12, (OK)
[    18.984] drmOpenByBusid: drmOpenMinor returns 12
[    18.984] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    18.984] (II) Loading sub module "exa"
[    18.984] (II) LoadModule: "exa"
[    18.984] (II) Loading /usr/lib/xorg/modules/libexa.so
[    19.025] (II) Module exa: vendor="X.Org Foundation"
[    19.025] 	compiled for 1.10.4, module version = 2.5.0
[    19.025] 	ABI class: X.Org Video Driver, version 10.0
[    19.025] (II) RADEON(0): KMS Color Tiling: enabled
[    19.025] (II) RADEON(0): KMS Pageflipping: enabled
[    19.025] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    19.045] (II) RADEON(0): Output LVDS has no monitor section
[    19.049] (II) RADEON(0): Output HDMI-0 has no monitor section
[    19.072] (II) RADEON(0): Output VGA-0 has no monitor section
[    19.092] (II) RADEON(0): EDID for output LVDS
[    19.092] (II) RADEON(0): Printing probed modes for output LVDS
[    19.092] (II) RADEON(0): Modeline "1366x768"x60.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
[    19.092] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    19.092] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    19.092] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    19.092] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    19.092] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    19.092] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    19.092] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    19.096] (II) RADEON(0): EDID for output HDMI-0
[    19.120] (II) RADEON(0): EDID for output VGA-0
[    19.120] (II) RADEON(0): Output LVDS connected
[    19.120] (II) RADEON(0): Output HDMI-0 disconnected
[    19.120] (II) RADEON(0): Output VGA-0 disconnected
[    19.120] (II) RADEON(0): Using exact sizes for initial modes
[    19.120] (II) RADEON(0): Output LVDS using initial mode 1366x768
[    19.120] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    19.120] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:20000000 visible:fba0000
[    19.120] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    19.120] (==) RADEON(0): DPI set to (96, 96)
[    19.120] (II) Loading sub module "fb"
[    19.120] (II) LoadModule: "fb"
[    19.120] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.166] (II) Module fb: vendor="X.Org Foundation"
[    19.166] 	compiled for 1.10.4, module version = 1.0.0
[    19.166] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.166] (II) Loading sub module "ramdac"
[    19.166] (II) LoadModule: "ramdac"
[    19.166] (II) Module "ramdac" already built-in
[    19.166] (II) UnloadModule: "vesa"
[    19.166] (II) Unloading vesa
[    19.166] (II) UnloadModule: "fbdev"
[    19.166] (II) Unloading fbdev
[    19.166] (II) UnloadModule: "fbdevhw"
[    19.166] (II) Unloading fbdevhw
[    19.166] (--) Depth 24 pixmap format is 32 bpp
[    19.166] (II) RADEON(0): [DRI2] Setup complete
[    19.166] (II) RADEON(0): [DRI2]   DRI driver: r600
[    19.166] (II) RADEON(0): Front buffer size: 4224K
[    19.166] (II) RADEON(0): VRAM usage limit set to 228096K
[    19.181] (==) RADEON(0): Backing store disabled
[    19.181] (II) RADEON(0): Direct rendering enabled
[    19.194] (II) RADEON(0): Setting EXA maxPitchBytes
[    19.194] (II) EXA(0): Driver allocated offscreen pixmaps
[    19.194] (II) EXA(0): Driver registered support for the following operations:
[    19.194] (II)         Solid
[    19.194] (II)         Copy
[    19.194] (II)         Composite (RENDER acceleration)
[    19.194] (II)         UploadToScreen
[    19.194] (II)         DownloadFromScreen
[    19.194] (II) RADEON(0): Acceleration enabled
[    19.194] (==) RADEON(0): DPMS enabled
[    19.194] (==) RADEON(0): Silken mouse enabled
[    19.214] (II) RADEON(0): Set up textured video
[    19.214] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    19.214] (II) RADEON(0): [XvMC] Extension initialized.
[    19.214] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.214] (--) RandR disabled
[    19.214] (II) Initializing built-in extension Generic Event Extension
[    19.214] (II) Initializing built-in extension SHAPE
[    19.214] (II) Initializing built-in extension MIT-SHM
[    19.214] (II) Initializing built-in extension XInputExtension
[    19.214] (II) Initializing built-in extension XTEST
[    19.214] (II) Initializing built-in extension BIG-REQUESTS
[    19.214] (II) Initializing built-in extension SYNC
[    19.214] (II) Initializing built-in extension XKEYBOARD
[    19.214] (II) Initializing built-in extension XC-MISC
[    19.214] (II) Initializing built-in extension SECURITY
[    19.214] (II) Initializing built-in extension XINERAMA
[    19.214] (II) Initializing built-in extension XFIXES
[    19.214] (II) Initializing built-in extension RENDER
[    19.214] (II) Initializing built-in extension RANDR
[    19.214] (II) Initializing built-in extension COMPOSITE
[    19.214] (II) Initializing built-in extension DAMAGE
[    19.214] (II) Initializing built-in extension GESTURE
[    19.222] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/r600_dri.so
[    20.784] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    20.784] (II) AIGLX: enabled GLX_INTEL_swap_event
[    20.784] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    20.784] (II) AIGLX: enabled GLX_SGI_make_current_read
[    20.784] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    20.785] (II) AIGLX: Loaded and initialized r600
[    20.785] (II) GLX: Initialized DRI2 GL provider for screen 0
[    20.802] (II) RADEON(0): Setting screen physical size to 361 x 203
[    20.998] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.018] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    21.018] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.018] (II) LoadModule: "evdev"
[    21.018] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.075] (II) Module evdev: vendor="X.Org Foundation"
[    21.075] 	compiled for 1.10.2, module version = 2.6.0
[    21.075] 	Module class: X.Org XInput Driver
[    21.075] 	ABI class: X.Org XInput driver, version 12.3
[    21.075] (II) Using input driver 'evdev' for 'Power Button'
[    21.075] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.075] (**) Power Button: always reports core events
[    21.075] (**) Power Button: Device: "/dev/input/event3"
[    21.075] (--) Power Button: Found keys
[    21.075] (II) Power Button: Configuring as keyboard
[    21.075] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    21.075] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.075] (**) Option "xkb_rules" "evdev"
[    21.076] (**) Option "xkb_model" "pc105"
[    21.076] (**) Option "xkb_layout" "es"
[    21.078] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    21.090] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    21.091] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.091] (II) Using input driver 'evdev' for 'Video Bus'
[    21.091] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.091] (**) Video Bus: always reports core events
[    21.091] (**) Video Bus: Device: "/dev/input/event6"
[    21.091] (--) Video Bus: Found keys
[    21.091] (II) Video Bus: Configuring as keyboard
[    21.091] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:3d/LNXVIDEO:00/input/input6/event6"
[    21.091] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    21.091] (**) Option "xkb_rules" "evdev"
[    21.091] (**) Option "xkb_model" "pc105"
[    21.091] (**) Option "xkb_layout" "es"
[    21.092] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.092] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.092] (II) Using input driver 'evdev' for 'Power Button'
[    21.092] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.092] (**) Power Button: always reports core events
[    21.092] (**) Power Button: Device: "/dev/input/event0"
[    21.092] (--) Power Button: Found keys
[    21.092] (II) Power Button: Configuring as keyboard
[    21.092] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    21.092] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.092] (**) Option "xkb_rules" "evdev"
[    21.092] (**) Option "xkb_model" "pc105"
[    21.092] (**) Option "xkb_layout" "es"
[    21.092] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    21.092] (II) No input driver/identifier specified (ignoring)
[    21.093] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    21.093] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    21.093] (II) Using input driver 'evdev' for 'Sleep Button'
[    21.093] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.093] (**) Sleep Button: always reports core events
[    21.093] (**) Sleep Button: Device: "/dev/input/event2"
[    21.093] (--) Sleep Button: Found keys
[    21.093] (II) Sleep Button: Configuring as keyboard
[    21.093] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    21.093] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    21.093] (**) Option "xkb_rules" "evdev"
[    21.093] (**) Option "xkb_model" "pc105"
[    21.093] (**) Option "xkb_layout" "es"
[    21.096] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event14)
[    21.096] (II) No input driver/identifier specified (ignoring)
[    21.100] (II) config/udev: Adding input device 2.4G Receiver (/dev/input/event8)
[    21.100] (**) 2.4G Receiver: Applying InputClass "evdev keyboard catchall"
[    21.100] (II) Using input driver 'evdev' for '2.4G Receiver'
[    21.100] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.100] (**) 2.4G Receiver: always reports core events
[    21.100] (**) 2.4G Receiver: Device: "/dev/input/event8"
[    21.100] (--) 2.4G Receiver: Found keys
[    21.100] (II) 2.4G Receiver: Configuring as keyboard
[    21.100] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input8/event8"
[    21.100] (II) XINPUT: Adding extended input device "2.4G Receiver" (type: KEYBOARD)
[    21.100] (**) Option "xkb_rules" "evdev"
[    21.100] (**) Option "xkb_model" "pc105"
[    21.100] (**) Option "xkb_layout" "es"
[    21.101] (II) config/udev: Adding input device 2.4G Receiver (/dev/input/event9)
[    21.101] (**) 2.4G Receiver: Applying InputClass "evdev pointer catchall"
[    21.101] (II) Using input driver 'evdev' for '2.4G Receiver'
[    21.101] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.101] (**) 2.4G Receiver: always reports core events
[    21.101] (**) 2.4G Receiver: Device: "/dev/input/event9"
[    21.101] (--) 2.4G Receiver: Found 9 mouse buttons
[    21.101] (--) 2.4G Receiver: Found scroll wheel(s)
[    21.101] (--) 2.4G Receiver: Found relative axes
[    21.101] (--) 2.4G Receiver: Found x and y relative axes
[    21.101] (II) 2.4G Receiver: Configuring as mouse
[    21.101] (II) 2.4G Receiver: Adding scrollwheel support
[    21.101] (**) 2.4G Receiver: YAxisMapping: buttons 4 and 5
[    21.101] (**) 2.4G Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.101] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input9/event9"
[    21.101] (II) XINPUT: Adding extended input device "2.4G Receiver" (type: MOUSE)
[    21.101] (II) 2.4G Receiver: initialized for relative axes.
[    21.101] (**) 2.4G Receiver: (accel) keeping acceleration scheme 1
[    21.101] (**) 2.4G Receiver: (accel) acceleration profile 0
[    21.101] (**) 2.4G Receiver: (accel) acceleration factor: 2.000
[    21.101] (**) 2.4G Receiver: (accel) acceleration threshold: 4
[    21.101] (II) config/udev: Adding input device 2.4G Receiver (/dev/input/mouse1)
[    21.101] (II) No input driver/identifier specified (ignoring)
[    21.102] (II) config/udev: Adding input device 2.4G Receiver (/dev/input/event10)
[    21.102] (**) 2.4G Receiver: Applying InputClass "evdev keyboard catchall"
[    21.102] (II) Using input driver 'evdev' for '2.4G Receiver'
[    21.102] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.102] (**) 2.4G Receiver: always reports core events
[    21.102] (**) 2.4G Receiver: Device: "/dev/input/event10"
[    21.102] (--) 2.4G Receiver: Found 1 mouse buttons
[    21.102] (--) 2.4G Receiver: Found scroll wheel(s)
[    21.102] (--) 2.4G Receiver: Found relative axes
[    21.102] (--) 2.4G Receiver: Found absolute axes
[    21.102] (II) evdev-grail: failed to open grail, no gesture support
[    21.102] (--) 2.4G Receiver: Found keys
[    21.102] (II) 2.4G Receiver: Configuring as mouse
[    21.102] (II) 2.4G Receiver: Configuring as keyboard
[    21.102] (II) 2.4G Receiver: Adding scrollwheel support
[    21.102] (**) 2.4G Receiver: YAxisMapping: buttons 4 and 5
[    21.102] (**) 2.4G Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.102] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.2/input/input10/event10"
[    21.102] (II) XINPUT: Adding extended input device "2.4G Receiver" (type: KEYBOARD)
[    21.102] (**) Option "xkb_rules" "evdev"
[    21.102] (**) Option "xkb_model" "pc105"
[    21.102] (**) Option "xkb_layout" "es"
[    21.103] (EE) 2.4G Receiver: failed to initialize for relative axes.
[    21.103] (II) 2.4G Receiver: initialized for absolute axes.
[    21.103] (**) 2.4G Receiver: (accel) keeping acceleration scheme 1
[    21.103] (**) 2.4G Receiver: (accel) acceleration profile 0
[    21.103] (**) 2.4G Receiver: (accel) acceleration factor: 2.000
[    21.103] (**) 2.4G Receiver: (accel) acceleration threshold: 4
[    21.104] (II) config/udev: Adding input device USB2.0 0.3M UVC WebCam (/dev/input/event11)
[    21.104] (**) USB2.0 0.3M UVC WebCam: Applying InputClass "evdev keyboard catchall"
[    21.104] (II) Using input driver 'evdev' for 'USB2.0 0.3M UVC WebCam'
[    21.104] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.104] (**) USB2.0 0.3M UVC WebCam: always reports core events
[    21.104] (**) USB2.0 0.3M UVC WebCam: Device: "/dev/input/event11"
[    21.104] (--) USB2.0 0.3M UVC WebCam: Found keys
[    21.104] (II) USB2.0 0.3M UVC WebCam: Configuring as keyboard
[    21.104] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input11/event11"
[    21.104] (II) XINPUT: Adding extended input device "USB2.0 0.3M UVC WebCam" (type: KEYBOARD)
[    21.104] (**) Option "xkb_rules" "evdev"
[    21.104] (**) Option "xkb_model" "pc105"
[    21.104] (**) Option "xkb_layout" "es"
[    21.105] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event12)
[    21.105] (II) No input driver/identifier specified (ignoring)
[    21.105] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event13)
[    21.105] (II) No input driver/identifier specified (ignoring)
[    21.107] (II) config/udev: Adding input device Asus Laptop extra buttons (/dev/input/event5)
[    21.107] (**) Asus Laptop extra buttons: Applying InputClass "evdev keyboard catchall"
[    21.107] (II) Using input driver 'evdev' for 'Asus Laptop extra buttons'
[    21.107] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.107] (**) Asus Laptop extra buttons: always reports core events
[    21.107] (**) Asus Laptop extra buttons: Device: "/dev/input/event5"
[    21.107] (--) Asus Laptop extra buttons: Found keys
[    21.107] (II) Asus Laptop extra buttons: Configuring as keyboard
[    21.107] (**) Option "config_info" "udev:/sys/devices/platform/asus_laptop/input/input5/event5"
[    21.107] (II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD)
[    21.107] (**) Option "xkb_rules" "evdev"
[    21.107] (**) Option "xkb_model" "pc105"
[    21.107] (**) Option "xkb_layout" "es"
[    21.108] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    21.108] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    21.108] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    21.108] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.108] (**) AT Translated Set 2 keyboard: always reports core events
[    21.108] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    21.108] (--) AT Translated Set 2 keyboard: Found keys
[    21.108] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    21.108] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    21.108] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    21.108] (**) Option "xkb_rules" "evdev"
[    21.108] (**) Option "xkb_model" "pc105"
[    21.108] (**) Option "xkb_layout" "es"
[    21.109] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event7)
[    21.109] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    21.109] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    21.109] (II) LoadModule: "synaptics"
[    21.109] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.186] (II) Module synaptics: vendor="X.Org Foundation"
[    21.186] 	compiled for 1.10.4, module version = 1.4.1
[    21.186] 	Module class: X.Org XInput Driver
[    21.186] 	ABI class: X.Org XInput driver, version 12.3
[    21.186] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    21.186] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.186] (**) ETPS/2 Elantech Touchpad: always reports core events
[    21.186] (**) Option "Device" "/dev/input/event7"
[    21.212] (--) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[    21.212] (--) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
[    21.212] (--) ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    21.212] (--) ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    21.212] (--) ETPS/2 Elantech Touchpad: buttons: left right double triple
[    21.244] (--) ETPS/2 Elantech Touchpad: touchpad found
[    21.244] (**) ETPS/2 Elantech Touchpad: always reports core events
[    21.320] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input7/event7"
[    21.320] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[    21.320] (**) ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    21.320] (**) ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    21.320] (**) ETPS/2 Elantech Touchpad: AccelFactor is now 0.147
[    21.320] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    21.320] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    21.320] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    21.320] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    21.321] (--) ETPS/2 Elantech Touchpad: touchpad found
[    21.321] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    21.321] (II) No input driver/identifier specified (ignoring)
[    39.746] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm

---

### Post by anforguiven on 2011-12-10
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

Espero que sea lo que me pediste. Esta por partes porque no me permitia poner todo junto. Espero que me puedas ayudar y gracias de antemano!

---

### Post by guillermolisi on 2011-12-11
Un problema que para mi es grave es que estas utilizando Ubuntu de 64 bits y el BIOS de tu maquina no tiene habilitada la funcion IOMMU que se encarga de gestionar direcciones de memoria por encima de los 3Gb RAM.

Las alternativas frente a esto es habilitar esa caracteristica en el BIOS y, si no la tiene expuesta (cosa que no me llamaria la atencion) reemplazar Ubuntu 64 bits por Ubuntu 32 pero usando kernel PAE para que puedas acceder a toda la RAM.

De hecho este mensaje lo estoy enviando desde una notebook con el mismo problema con IOMMU y despues de renegar y leer por el campeonato termine haciendo la segunda alternativa. A partir de eso se me acabaron los problemas y disfruto a pleno de la maquina.

Mas alla de esto y suponiendo que logras solucionar los problemas de administracion de energia, con los sintomas que mencionaste, vas a tener problemas de estabilidad ya que la gestion de memoria por encima de los 3Gb estara fuera de control.

Supongo que volver a instalar una version de 32 bits y usar el kernel PAE no te hara mal despues de las quichicientas veces que debes haber reinstalado. Seria una muy buena prueba.

---

### Post by anforguiven on 2011-12-11
> **guillermolisi said:**
> Un problema que para mi es grave es que estas utilizando Ubuntu de 64 bits y el BIOS de tu maquina no tiene habilitada la funcion IOMMU que se encarga de gestionar direcciones de memoria por encima de los 3Gb RAM.

Las alternativas frente a esto es habilitar esa caracteristica en el BIOS y, si no la tiene expuesta (cosa que no me llamaria la atencion) reemplazar Ubuntu 64 bits por Ubuntu 32 pero usando kernel PAE para que puedas acceder a toda la RAM.

De hecho este mensaje lo estoy enviando desde una notebook con el mismo problema con IOMMU y despues de renegar y leer por el campeonato termine haciendo la segunda alternativa. A partir de eso se me acabaron los problemas y disfruto a pleno de la maquina.

Mas alla de esto y suponiendo que logras solucionar los problemas de administracion de energia, con los sintomas que mencionaste, vas a tener problemas de estabilidad ya que la gestion de memoria por encima de los 3Gb estara fuera de control.

Supongo que volver a instalar una version de 32 bits y usar el kernel PAE no te hara mal despues de las quichicientas veces que debes haber reinstalado. Seria una muy buena prueba.

No tengo nada como eso en el BIOS, ya estoy descargando la versión de 32 bit y la instalo con PAE habilitado,con respecto a lo que me decís de las re instalaciones es tal cual! no me acuerdo ya las veces que reinstale y las distros que probé!

Ojala funcione y se solucione, pruebo y te cuento GRACIAS!

---

### Post by anforguiven on 2011-12-11
> **anforguiven said:**
> No tengo nada como eso en el BIOS, ya estoy descargando la versión de 32 bit y la instalo con PAE habilitado,con respecto a lo que me decís de las re instalaciones es tal cual! no me acuerdo ya las veces que reinstale y las distros que probé!

Ojala funcione y se solucione, pruebo y te cuento GRACIAS!



Lamentablemente sigo con el mismo problema luego de reinstalar Ubuntu x32 en modo PAE, lo que si noto diferente es que la maquina trabaja mucho mas fría y todo en general esta mas fluido,si no es molestia te paso nuevamente lo que me pediste(por si sirve de algo)

---

### Post by anforguiven on 2011-12-11
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

marcos@ASUS:~$ sudo lshw
[sudo] password for marcos: 
asus                      
    description: Notebook
    product: K52De ()
    vendor: ASUSTeK Computer Inc.
    version: 1.0
    serial: B2N0AS15171907
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook uuid=006F86F3-BA3D-E081-3575-BCAEC5647FAB
  *-core
       description: Motherboard
       product: K52De
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: K52De.208
          date: 12/10/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II N830 Triple-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.5.3
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 3698MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=3 enabledcores=3
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 384KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 1536KiB
             capabilities: internal varies data
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 0
             serial: 66B2BFB0
             slot: A1_DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 1
             serial: 66B2BFAF
             slot: A1_DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fdf00000-fe8fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Manhattan [Mobility Radeon HD 5400 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:44 memory:d0000000-dfffffff memory:fdf20000-fdf3ffff ioport:e000(size=256) memory:fdf00000-fdf1ffff
           *-multimedia
                description: Audio device
                product: Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:45 memory:fdf40000-fdf43fff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:fea00000-feafffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 01
                serial: 48:5d:60:b3:4b:3b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.0.0-14-generic-pae firmware=N/A ip=192.168.43.127 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:fea00000-fea0ffff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:fe900000-fe9fffff
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:fe907000-fe9070ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:05:00.2
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:fe906000-fe9060ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:05:00.3
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:18 memory:fe905000-fe9050ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:05:00.4
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:fe904000-fe9040ff
           *-network
                description: Ethernet interface
                product: JMC250 PCI Express Gigabit Ethernet Controller
                vendor: JMicron Technology Corp.
                physical id: 0.5
                bus info: pci@0000:05:00.5
                logical name: eth0
                version: 03
                serial: bc:ae:c5:64:7f:ab
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:46 memory:fe900000-fe903fff ioport:d100(size=128) ioport:d000(size=256)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:43 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:feb0a000-feb0a3ff
           *-disk
                description: ATA Disk
                product: SAMSUNG HN-M101M
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 2AR1
                serial: S2R8J9FB600108
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009b92c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: e6ef367d-4ddc-4d9e-a1ce-ae8b2a3d52ae
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-12-11 13:38:50 filesystem=ext4 lastmountpoint=/ modified=2011-12-11 14:08:25 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,commit=600,barrier=1,data=ordered mounted=2011-12-11 20:09:00 state=mounted
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /home
                   version: 1.0
                   serial: e474de27-f0a1-4c91-af77-806ae214621b
                   size: 910GiB
                   capacity: 910GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-12-11 13:38:53 filesystem=ext4 lastmountpoint=/home modified=2011-12-11 20:09:00 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,commit=600,barrier=1,data=ordered mounted=2011-12-11 20:09:00 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 1952MiB
                   capacity: 1952MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1952MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT34N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AS00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb09000-feb09fff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb08000-feb080ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb07000-feb07fff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb06000-feb060ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
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
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:feb00000-feb03fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
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
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb05000-feb05fff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:feb04000-feb040ff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
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
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by anforguiven on 2011-12-11
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

marcos@ASUS:~$ sudo lspci
[sudo] password for marcos: 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
05:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)

---

### Post by anforguiven on 2011-12-11
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

/var/log/dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic-pae (buildd@palmer) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 (Ubuntu 3.0.0-14.23-generic-pae 3.0.9)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afcc3000 (usable)
[    0.000000]  BIOS-e820: 00000000afcc3000 - 00000000afd0d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd0d000 - 00000000afd1b000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afd1b000 - 00000000afd2c000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd2c000 - 00000000afd34000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd34000 - 00000000afd44000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd44000 - 00000000afd45000 (usable)
[    0.000000]  BIOS-e820: 00000000afd45000 - 00000000afd47000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd47000 - 00000000afd48000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd48000 - 00000000afd4b000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd4b000 - 00000000afd51000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd51000 - 00000000afd71000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd71000 - 00000000afd72000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd72000 - 00000000afd87000 (reserved)
[    0.000000]  BIOS-e820: 00000000afd87000 - 00000000afd8e000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afd8e000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed61000 - 00000000fed71000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed80000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100001000 - 0000000150000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: ASUSTeK Computer Inc.         K52De/K52De, BIOS K52De.208 12/10/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x150000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF00000000 write-back
[    0.000000]   1 base 0000AFF00000 mask FFFFFFF00000 uncachable
[    0.000000]   2 base 0000B0000000 mask FFFFF0000000 uncachable
[    0.000000]   3 base 0000C0000000 mask FFFFC0000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000150000000 aka 5376M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 2815MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2816MB, range: 256MB, type UC
[    0.000000] reg 3, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 2815M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2815MB, range: 1MB, type UC
[    0.000000] e820 update range: 00000000aff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 365e4000 - 372ea000
[    0.000000] ACPI: RSDP 000f0410 00024 (v03 _ASUS_)
[    0.000000] ACPI: XSDT afd0d080 00054 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FACP afd19b60 000F4 (v04 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xAFD4BF40/0x00000000AFD4BF80, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110413/tbfadt-560)
[    0.000000] ACPI: DSDT afd0d168 0C9F3 (v02 _ASUS_ Notebook 00000000 INTL 20051117)
[    0.000000] ACPI: FACS afd4bf40 00040
[    0.000000] ACPI: APIC afd19c58 00072 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: ECDT afd19cd0 000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000003)
[    0.000000] ACPI: MCFG afd19d98 0003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT afd19dd8 007AD (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: HPET afd1a588 00038 (v01 _ASUS_ Notebook 01072009 AMI  00000003)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4484MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00150000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000afcc3
[    0.000000]     0: 0x000afd44 -> 0x000afd45
[    0.000000]     0: 0x000afd8e -> 0x000aff00
[    0.000000]     0: 0x00100001 -> 0x00150000
[    0.000000] On node 0 totalpages: 1048003
[    0.000000] free_area_init_node: node 0, pgdat c17ee1c0, node_mem_map f3be4200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8969 pages used for memmap
[    0.000000]   HighMem zone: 810798 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:4ed00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u524288
[    0.000000] pcpu-alloc: s29952 r0 d23296 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1037250
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic-pae root=UUID=e6ef367d-4ddc-4d9e-a1ce-ae8b2a3d52ae ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 22019840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00150000)
[    0.000000] Memory: 4103228k/5505024k available (5499k kernel code, 88784k reserved, 2665k data, 720k init, 3279068k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17fa000 - 0xc18ae000   ( 720 kB)
[    0.000000]       .data : 0xc155efb0 - 0xc17f94c0   (2665 kB)
[    0.000000]       .text : 0xc1000000 - 0xc155efb0   (5499 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2094.744 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4189.48 BogoMIPS (lpj=8378976)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004033] Security Framework initialized
[    0.004051] AppArmor: AppArmor initialized
[    0.004054] Yama: becoming mindful.
[    0.004116] Mount-cache hash table entries: 512
[    0.004244] Initializing cgroup subsys cpuacct
[    0.004251] Initializing cgroup subsys memory
[    0.004260] Initializing cgroup subsys devices
[    0.004263] Initializing cgroup subsys freezer
[    0.004266] Initializing cgroup subsys net_cls
[    0.004269] Initializing cgroup subsys blkio
[    0.004277] Initializing cgroup subsys perf_event
[    0.004304] CPU: Physical Processor ID: 0
[    0.004306] CPU: Processor Core ID: 0
[    0.004310] mce: CPU supports 6 MCE banks
[    0.004319] using AMD E400 aware idle routine
[    0.008361] ACPI: Core revision 20110413
[    0.020012] ftrace: allocating 25575 entries in 51 pages
[    0.024066] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024353] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067643] CPU0: AMD Phenom(tm) II N830 Triple-Core Processor stepping 03
[    0.068003] Performance Events: AMD PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              48
[    0.068003] ... generic registers:      4
[    0.068003] ... value mask:             0000ffffffffffff
[    0.068003] ... max period:             00007fffffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000000000f
[    0.068003] CPU 1 irqstacks, hard=f74d2000 soft=f74d4000
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.156020] System has AMD C1E enabled
[    0.156029] Switch to broadcast mode on CPU1
[    0.156076] CPU 2 irqstacks, hard=f74de000 soft=f74e0000
[    0.156078]  #2
[    0.156079] smpboot cpu 2: start_ip = 9a000
[    0.008000] Initializing CPU#2
[    0.248025] Brought up 3 CPUs
[    0.248028] Total of 3 processors activated (12568.55 BogoMIPS).
[    0.248026] Switch to broadcast mode on CPU2
[    0.248516] Switch to broadcast mode on CPU0
[    0.248516] devtmpfs: initialized
[    0.248516] PM: Registering ACPI NVS region at afcc3000 (303104 bytes)
[    0.248516] PM: Registering ACPI NVS region at afd2c000 (32768 bytes)
[    0.248516] PM: Registering ACPI NVS region at afd47000 (4096 bytes)
[    0.248516] PM: Registering ACPI NVS region at afd4b000 (24576 bytes)
[    0.248516] PM: Registering ACPI NVS region at afd71000 (4096 bytes)
[    0.248516] PM: Registering ACPI NVS region at afd87000 (28672 bytes)
[    0.250038] print_constraints: dummy: 
[    0.250060] Time: 23:08:44  Date: 12/11/11
[    0.250096] NET: Registered protocol family 16
[    0.250200] EISA bus registered
[    0.250205] node 0 link 0: io port [d000, ffff]
[    0.250208] TOM: 00000000b0000000 aka 2816M
[    0.250210] Fam 10h mmconf [e0000000, efffffff]
[    0.250214] node 0 link 0: mmio [a0000, bffff]
[    0.250217] node 0 link 0: mmio [b0000000, dfffffff]
[    0.250220] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.250223] node 0 link 0: mmio [f0000000, ff7fffff]
[    0.250225] TOM2: 0000000150000000 aka 5376M
[    0.250228] bus: [00, ff] on node 0 link 0
[    0.250231] bus: 00 index 0 [io  0x0000-0xffff]
[    0.250233] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.250236] bus: 00 index 2 [mem 0xb0000000-0xdfffffff]
[    0.250238] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.250240] bus: 00 index 4 [mem 0x150000000-0xfcffffffff]
[    0.250242] bus: [00, 06] on node 0 link 0
[    0.250251] Extended Config Space enabled on 1 nodes
[    0.250269] ACPI: bus type pci registered
[    0.250105] Trying to unpack rootfs image as initramfs...
[    0.250333] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.250337] PCI: not using MMCONFIG
[    0.282689] PCI: Using configuration type 1 for base access
[    0.282691] PCI: Using configuration type 1 for extended access
[    0.283479] bio: create slab <bio-0> at 0
[    0.283479] ACPI: EC: EC description table is found, configuring boot EC
[    0.283479] ACPI: EC: Look up EC in DSDT
[    0.283886] ACPI: Executed 2 blocks of module-level executable AML code
[    0.286624] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.549354] Freeing initrd memory: 13336k freed
[    0.572351] ACPI: Interpreter enabled
[    0.572358] ACPI: (supports S0 S3 S4 S5)
[    0.572379] ACPI: Using IOAPIC for interrupt routing
[    0.572554] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.572595] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.572597] PCI: Using MMCONFIG for extended config space
[    0.581120] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.581368] ACPI: No dock devices found.
[    0.581370] HEST: Table not found.
[    0.581374] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.581539] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.581674] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.581677] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.581680] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.581682] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000fffff]
[    0.581685] pci_root PNP0A03:00: host bridge window [mem 0xb0000000-0xffffffff]
[    0.581702] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    0.581752] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
[    0.581781] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.581784] pci 0000:00:02.0: PME# disabled
[    0.581803] pci 0000:00:04.0: [1022:9604] type 1 class 0x000604
[    0.581830] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.581833] pci 0000:00:04.0: PME# disabled
[    0.581847] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
[    0.581874] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.581877] pci 0000:00:05.0: PME# disabled
[    0.581914] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.581935] pci 0000:00:11.0: reg 10: [io  0xf090-0xf097]
[    0.581944] pci 0000:00:11.0: reg 14: [io  0xf080-0xf083]
[    0.581954] pci 0000:00:11.0: reg 18: [io  0xf070-0xf077]
[    0.581963] pci 0000:00:11.0: reg 1c: [io  0xf060-0xf063]
[    0.581973] pci 0000:00:11.0: reg 20: [io  0xf050-0xf05f]
[    0.581983] pci 0000:00:11.0: reg 24: [mem 0xfeb0a000-0xfeb0a3ff]
[    0.582035] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.582048] pci 0000:00:12.0: reg 10: [mem 0xfeb09000-0xfeb09fff]
[    0.582114] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.582133] pci 0000:00:12.2: reg 10: [mem 0xfeb08000-0xfeb080ff]
[    0.582199] pci 0000:00:12.2: supports D1 D2
[    0.582201] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.582205] pci 0000:00:12.2: PME# disabled
[    0.582225] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.582238] pci 0000:00:13.0: reg 10: [mem 0xfeb07000-0xfeb07fff]
[    0.582304] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.582322] pci 0000:00:13.2: reg 10: [mem 0xfeb06000-0xfeb060ff]
[    0.582388] pci 0000:00:13.2: supports D1 D2
[    0.582390] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.582394] pci 0000:00:13.2: PME# disabled
[    0.582414] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.582486] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.582507] pci 0000:00:14.2: reg 10: [mem 0xfeb00000-0xfeb03fff 64bit]
[    0.582562] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.582566] pci 0000:00:14.2: PME# disabled
[    0.582578] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.582648] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.582694] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    0.582707] pci 0000:00:16.0: reg 10: [mem 0xfeb05000-0xfeb05fff]
[    0.582773] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.582791] pci 0000:00:16.2: reg 10: [mem 0xfeb04000-0xfeb040ff]
[    0.582857] pci 0000:00:16.2: supports D1 D2
[    0.582859] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.582863] pci 0000:00:16.2: PME# disabled
[    0.582881] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.582900] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.582914] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.582929] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.582946] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.582996] pci 0000:01:00.0: [1002:68e0] type 0 class 0x000300
[    0.583010] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.583020] pci 0000:01:00.0: reg 18: [mem 0xfdf20000-0xfdf3ffff 64bit]
[    0.583028] pci 0000:01:00.0: reg 20: [io  0xe000-0xe0ff]
[    0.583041] pci 0000:01:00.0: reg 30: [mem 0xfdf00000-0xfdf1ffff pref]
[    0.583058] pci 0000:01:00.0: supports D1 D2
[    0.583077] pci 0000:01:00.1: [1002:aa68] type 0 class 0x000403
[    0.583090] pci 0000:01:00.1: reg 10: [mem 0xfdf40000-0xfdf43fff 64bit]
[    0.583133] pci 0000:01:00.1: supports D1 D2
[    0.592065] pci 0000:00:02.0: PCI bridge to [bus 01-03]
[    0.592072] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.592076] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfe8fffff]
[    0.592081] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.592124] pci 0000:04:00.0: [168c:002b] type 0 class 0x000280
[    0.592144] pci 0000:04:00.0: reg 10: [mem 0xfea00000-0xfea0ffff 64bit]
[    0.592211] pci 0000:04:00.0: supports D1
[    0.592214] pci 0000:04:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.592218] pci 0000:04:00.0: PME# disabled
[    0.600066] pci 0000:00:04.0: PCI bridge to [bus 04-04]
[    0.600072] pci 0000:00:04.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.600076] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.600081] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.600123] pci 0000:05:00.0: [197b:2382] type 0 class 0x000880
[    0.600142] pci 0000:05:00.0: reg 10: [mem 0xfe907000-0xfe9070ff]
[    0.600258] pci 0000:05:00.2: [197b:2381] type 0 class 0x000805
[    0.600274] pci 0000:05:00.2: reg 10: [mem 0xfe906000-0xfe9060ff]
[    0.600383] pci 0000:05:00.3: [197b:2383] type 0 class 0x000880
[    0.600399] pci 0000:05:00.3: reg 10: [mem 0xfe905000-0xfe9050ff]
[    0.600508] pci 0000:05:00.4: [197b:2384] type 0 class 0x000880
[    0.600524] pci 0000:05:00.4: reg 10: [mem 0xfe904000-0xfe9040ff]
[    0.600634] pci 0000:05:00.5: [197b:0250] type 0 class 0x000200
[    0.600650] pci 0000:05:00.5: reg 10: [mem 0xfe900000-0xfe903fff]
[    0.600671] pci 0000:05:00.5: reg 18: [io  0xd100-0xd17f]
[    0.600682] pci 0000:05:00.5: reg 1c: [io  0xd000-0xd0ff]
[    0.600741] pci 0000:05:00.5: PME# supported from D0 D3hot D3cold
[    0.600746] pci 0000:05:00.5: PME# disabled
[    0.608073] pci 0000:00:05.0: PCI bridge to [bus 05-05]
[    0.608079] pci 0000:00:05.0:   bridge window [io  0xd000-0xdfff]
[    0.608083] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.608087] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.608154] pci 0000:00:14.4: PCI bridge to [bus 06-06] (subtractive decode)
[    0.608159] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.608164] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.608169] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.608172] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.608175] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.608178] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.608181] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000fffff] (subtractive decode)
[    0.608184] pci 0000:00:14.4:   bridge window [mem 0xb0000000-0xffffffff] (subtractive decode)
[    0.608198] pci_bus 0000:00: on NUMA node 0
[    0.608203] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.608425] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.608486] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.608521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.608657]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.608748]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x00
[    0.608750] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.609714] ACPI: PCI Interrupt Link [LN24] (IRQs *24)
[    0.609744] ACPI: PCI Interrupt Link [LN25] (IRQs *25)
[    0.609773] ACPI: PCI Interrupt Link [LN26] (IRQs *26)
[    0.609802] ACPI: PCI Interrupt Link [LN27] (IRQs *27)
[    0.609831] ACPI: PCI Interrupt Link [LN28] (IRQs *28)
[    0.609859] ACPI: PCI Interrupt Link [LN29] (IRQs *29)
[    0.609888] ACPI: PCI Interrupt Link [LN30] (IRQs *30)
[    0.609916] ACPI: PCI Interrupt Link [LN31] (IRQs *31)
[    0.609945] ACPI: PCI Interrupt Link [LN32] (IRQs *32)
[    0.609974] ACPI: PCI Interrupt Link [LN33] (IRQs *33)
[    0.610003] ACPI: PCI Interrupt Link [LN34] (IRQs *34)
[    0.610032] ACPI: PCI Interrupt Link [LN35] (IRQs *35)
[    0.610061] ACPI: PCI Interrupt Link [LN36] (IRQs *36)
[    0.610090] ACPI: PCI Interrupt Link [LN37] (IRQs *37)
[    0.610119] ACPI: PCI Interrupt Link [LN38] (IRQs *38)
[    0.610148] ACPI: PCI Interrupt Link [LN39] (IRQs *39)
[    0.610177] ACPI: PCI Interrupt Link [LN40] (IRQs *40)
[    0.610206] ACPI: PCI Interrupt Link [LN41] (IRQs *41)
[    0.610235] ACPI: PCI Interrupt Link [LN42] (IRQs *42)
[    0.610265] ACPI: PCI Interrupt Link [LN43] (IRQs *43)
[    0.610294] ACPI: PCI Interrupt Link [LN44] (IRQs *44)
[    0.610323] ACPI: PCI Interrupt Link [LN45] (IRQs *45)
[    0.610352] ACPI: PCI Interrupt Link [LN46] (IRQs *46)
[    0.610384] ACPI: PCI Interrupt Link [LN47] (IRQs *47)
[    0.610413] ACPI: PCI Interrupt Link [LN48] (IRQs *48)
[    0.610443] ACPI: PCI Interrupt Link [LN49] (IRQs *49)
[    0.610473] ACPI: PCI Interrupt Link [LN50] (IRQs *50)
[    0.610502] ACPI: PCI Interrupt Link [LN51] (IRQs *51)
[    0.610532] ACPI: PCI Interrupt Link [LN52] (IRQs *52)
[    0.610561] ACPI: PCI Interrupt Link [LN53] (IRQs *53)
[    0.610591] ACPI: PCI Interrupt Link [LN54] (IRQs *54)
[    0.610620] ACPI: PCI Interrupt Link [LN55] (IRQs *55)
[    0.610656] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
[    0.610715] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
[    0.610776] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
[    0.610836] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 14 15) *0
[    0.610884] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
[    0.610920] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
[    0.610957] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
[    0.610993] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
[    0.611094] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.611100] vgaarb: loaded
[    0.611101] vgaarb: bridge control possible 0000:01:00.0
[    0.611293] SCSI subsystem initialized
[    0.612087] libata version 3.00 loaded.
[    0.612148] usbcore: registered new interface driver usbfs
[    0.612159] usbcore: registered new interface driver hub
[    0.612173] usbcore: registered new device driver usb
[    0.612173] PCI: Using ACPI for IRQ routing
[    0.619702] PCI: pci_cache_line_size set to 64 bytes
[    0.619800] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.619803] reserve RAM buffer: 00000000afcc3000 - 00000000afffffff 
[    0.619808] reserve RAM buffer: 00000000afd45000 - 00000000afffffff 
[    0.619812] reserve RAM buffer: 00000000aff00000 - 00000000afffffff 
[    0.619914] NetLabel: Initializing
[    0.619916] NetLabel:  domain hash size = 128
[    0.619917] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.619927] NetLabel:  unlabeled traffic allowed by default
[    0.619994] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.619999] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.621078] Switching to clocksource hpet
[    0.626026] Switched to NOHz mode on CPU #2
[    0.626033] Switched to NOHz mode on CPU #0
[    0.626038] Switched to NOHz mode on CPU #1
[    0.629879] AppArmor: AppArmor Filesystem Enabled
[    0.629906] pnp: PnP ACPI init
[    0.629922] ACPI: bus type pnp registered
[    0.630023] pnp 00:00: [bus 00-ff]
[    0.630026] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.630029] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.630031] pnp 00:00: [io  0x0d00-0xffff window]
[    0.630034] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.630037] pnp 00:00: [mem 0x000c0000-0x000fffff window]
[    0.630039] pnp 00:00: [mem 0xb0000000-0xffffffff window]
[    0.630118] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.630156] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.630209] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.630212] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.630729] pnp 00:02: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.630732] pnp 00:02: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.630774] system 00:02: Plug and Play ACPI device, IDs PNP0c02

---

### Post by anforguiven on 2011-12-11
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

/var/log/dmesg (parte2)
(active)
[    0.631108] pnp 00:03: [io  0x0010-0x001f]
[    0.631112] pnp 00:03: [io  0x0022-0x003f]
[    0.631115] pnp 00:03: [io  0x0062-0x0063]
[    0.631117] pnp 00:03: [io  0x0065-0x006f]
[    0.631119] pnp 00:03: [io  0x0072-0x007f]
[    0.631120] pnp 00:03: [io  0x0080]
[    0.631122] pnp 00:03: [io  0x0084-0x0086]
[    0.631124] pnp 00:03: [io  0x0088]
[    0.631126] pnp 00:03: [io  0x008c-0x008e]
[    0.631128] pnp 00:03: [io  0x0090-0x009f]
[    0.631130] pnp 00:03: [io  0x00a2-0x00bf]
[    0.631131] pnp 00:03: [io  0x00b1]
[    0.631133] pnp 00:03: [io  0x00e0-0x00ef]
[    0.631135] pnp 00:03: [io  0x04d0-0x04d1]
[    0.631137] pnp 00:03: [io  0x040b]
[    0.631139] pnp 00:03: [io  0x04d6]
[    0.631141] pnp 00:03: [io  0x0c00-0x0c01]
[    0.631143] pnp 00:03: [io  0x0c14]
[    0.631144] pnp 00:03: [io  0x0c50-0x0c51]
[    0.631146] pnp 00:03: [io  0x0c52]
[    0.631148] pnp 00:03: [io  0x0c6c]
[    0.631150] pnp 00:03: [io  0x0c6f]
[    0.631152] pnp 00:03: [io  0x0cd0-0x0cd1]
[    0.631154] pnp 00:03: [io  0x0cd2-0x0cd3]
[    0.631155] pnp 00:03: [io  0x0cd4-0x0cd5]
[    0.631157] pnp 00:03: [io  0x0cd6-0x0cd7]
[    0.631159] pnp 00:03: [io  0x0cd8-0x0cdf]
[    0.631161] pnp 00:03: [io  0x0800-0x089f]
[    0.631163] pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
[    0.631166] pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
[    0.631168] pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
[    0.631170] pnp 00:03: [io  0x0900-0x090f]
[    0.631172] pnp 00:03: [io  0x0910-0x091f]
[    0.631174] pnp 00:03: [io  0xfe00-0xfefe]
[    0.631176] pnp 00:03: [io  0x0060-0x005f disabled]
[    0.631178] pnp 00:03: [io  0x0064-0x0063 disabled]
[    0.631181] pnp 00:03: [mem 0xfec00000-0xfec00fff]
[    0.631183] pnp 00:03: [mem 0xfee00000-0xfee00fff]
[    0.631185] pnp 00:03: [mem 0xfed80000-0xfed8ffff]
[    0.631187] pnp 00:03: [mem 0xfed61000-0xfed70fff]
[    0.631189] pnp 00:03: [mem 0xfec10000-0xfec10fff]
[    0.631191] pnp 00:03: [mem 0xfed00000-0xfed00fff]
[    0.631194] pnp 00:03: [mem 0xff800000-0xffffffff]
[    0.631306] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.631311] system 00:03: [io  0x040b] has been reserved
[    0.631314] system 00:03: [io  0x04d6] has been reserved
[    0.631316] system 00:03: [io  0x0c00-0x0c01] has been reserved
[    0.631319] system 00:03: [io  0x0c14] has been reserved
[    0.631322] system 00:03: [io  0x0c50-0x0c51] has been reserved
[    0.631324] system 00:03: [io  0x0c52] has been reserved
[    0.631327] system 00:03: [io  0x0c6c] has been reserved
[    0.631329] system 00:03: [io  0x0c6f] has been reserved
[    0.631332] system 00:03: [io  0x0cd0-0x0cd1] has been reserved
[    0.631334] system 00:03: [io  0x0cd2-0x0cd3] has been reserved
[    0.631337] system 00:03: [io  0x0cd4-0x0cd5] has been reserved
[    0.631340] system 00:03: [io  0x0cd6-0x0cd7] has been reserved
[    0.631342] system 00:03: [io  0x0cd8-0x0cdf] has been reserved
[    0.631345] system 00:03: [io  0x0800-0x089f] has been reserved
[    0.631348] system 00:03: [io  0x0900-0x090f] has been reserved
[    0.631351] system 00:03: [io  0x0910-0x091f] has been reserved
[    0.631354] system 00:03: [io  0xfe00-0xfefe] has been reserved
[    0.631358] system 00:03: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.631361] system 00:03: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.631364] system 00:03: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.631367] system 00:03: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.631370] system 00:03: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.631373] system 00:03: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.631376] system 00:03: [mem 0xff800000-0xffffffff] has been reserved
[    0.631380] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.631397] pnp 00:04: [dma 4]
[    0.631399] pnp 00:04: [io  0x0000-0x000f]
[    0.631401] pnp 00:04: [io  0x0081-0x0083]
[    0.631403] pnp 00:04: [io  0x0087]
[    0.631405] pnp 00:04: [io  0x0089-0x008b]
[    0.631407] pnp 00:04: [io  0x008f]
[    0.631409] pnp 00:04: [io  0x00c0-0x00df]
[    0.631433] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.631444] pnp 00:05: [io  0x0070-0x0071]
[    0.631453] pnp 00:05: [irq 8]
[    0.631477] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.631484] pnp 00:06: [io  0x0061]
[    0.631507] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.631526] pnp 00:07: [io  0x0010-0x001f]
[    0.631527] pnp 00:07: [io  0x0022-0x003f]
[    0.631529] pnp 00:07: [io  0x0044-0x005f]
[    0.631531] pnp 00:07: [io  0x0062-0x0063]
[    0.631533] pnp 00:07: [io  0x0065-0x006f]
[    0.631535] pnp 00:07: [io  0x0072-0x007f]
[    0.631537] pnp 00:07: [io  0x0080]
[    0.631539] pnp 00:07: [io  0x0084-0x0086]
[    0.631541] pnp 00:07: [io  0x0088]
[    0.631543] pnp 00:07: [io  0x008c-0x008e]
[    0.631544] pnp 00:07: [io  0x0090-0x009f]
[    0.631546] pnp 00:07: [io  0x00a2-0x00bf]
[    0.631548] pnp 00:07: [io  0x00e0-0x00ef]
[    0.631550] pnp 00:07: [io  0x04d0-0x04d1]
[    0.631599] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.631602] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.631610] pnp 00:08: [io  0x00f0-0x00ff]
[    0.631619] pnp 00:08: [irq 13]
[    0.631644] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.631697] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.631709] pnp 00:0a: [io  0x0240-0x0259]
[    0.631753] system 00:0a: [io  0x0240-0x0259] has been reserved
[    0.631756] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.631803] pnp 00:0b: [irq 12]
[    0.631831] pnp 00:0b: Plug and Play ACPI device, IDs ETD0001 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.631854] pnp 00:0c: [io  0x0060]
[    0.631856] pnp 00:0c: [io  0x0064]
[    0.631860] pnp 00:0c: [irq 1]
[    0.631886] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.632302] pnp 00:0d: [mem 0xfed00000-0xfed003ff]
[    0.632356] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.632362] pnp: PnP ACPI: found 14 devices
[    0.632364] ACPI: ACPI bus type pnp unregistered
[    0.632367] PnPBIOS: Disabled by ACPI PNP
[    0.668371] PCI: max bus depth: 1 pci_try_num: 2
[    0.668392] pci 0000:00:02.0: PCI bridge to [bus 01-03]
[    0.668395] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.668399] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfe8fffff]
[    0.668403] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.668407] pci 0000:00:04.0: PCI bridge to [bus 04-04]
[    0.668409] pci 0000:00:04.0:   bridge window [io  disabled]
[    0.668412] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.668415] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    0.668420] pci 0000:00:05.0: PCI bridge to [bus 05-05]
[    0.668422] pci 0000:00:05.0:   bridge window [io  0xd000-0xdfff]
[    0.668426] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.668429] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.668433] pci 0000:00:14.4: PCI bridge to [bus 06-06]
[    0.668435] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.668440] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.668444] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.668462] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.668466] pci 0000:00:02.0: setting latency timer to 64
[    0.668474] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.668478] pci 0000:00:04.0: setting latency timer to 64
[    0.668485] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.668488] pci 0000:00:05.0: setting latency timer to 64
[    0.668496] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.668498] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.668501] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.668504] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000fffff]
[    0.668506] pci_bus 0000:00: resource 8 [mem 0xb0000000-0xffffffff]
[    0.668509] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.668511] pci_bus 0000:01: resource 1 [mem 0xfdf00000-0xfe8fffff]
[    0.668514] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.668517] pci_bus 0000:04: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.668520] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
[    0.668522] pci_bus 0000:05: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.668525] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.668527] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.668530] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.668532] pci_bus 0000:06: resource 7 [mem 0x000c0000-0x000fffff]
[    0.668535] pci_bus 0000:06: resource 8 [mem 0xb0000000-0xffffffff]
[    0.668573] NET: Registered protocol family 2
[    0.668631] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.668831] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.669325] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.669571] TCP: Hash tables configured (established 131072 bind 65536)
[    0.669573] TCP reno registered
[    0.669576] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.669585] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.669674] NET: Registered protocol family 1
[    0.720203] pci 0000:01:00.0: Boot video device
[    0.720223] PCI: CLS 64 bytes, default 64
[    0.720588] audit: initializing netlink socket (disabled)
[    0.720597] type=2000 audit(1323644924.720:1): initialized
[    0.749317] highmem bounce pool size: 64 pages
[    0.749323] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.762727] VFS: Disk quotas dquot_6.5.2
[    0.762802] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.763588] fuse init (API version 7.16)
[    0.763692] msgmni has been set to 1635
[    0.764428] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.764541] io scheduler noop registered
[    0.764545] io scheduler deadline registered
[    0.764577] io scheduler cfq registered (default)
[    0.764704] pcieport 0000:00:02.0: setting latency timer to 64
[    0.764735] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.764778] pcieport 0000:00:04.0: setting latency timer to 64
[    0.764801] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    0.764840] pcieport 0000:00:05.0: setting latency timer to 64
[    0.764863] pcieport 0000:00:05.0: irq 42 for MSI/MSI-X
[    0.764921] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.764944] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.765054] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.765098] ACPI: AC Adapter [AC0] (off-line)
[    0.765206] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.765211] ACPI: Power Button [PWRB]
[    0.765253] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.766543] ACPI: Lid Switch [LID]
[    0.766606] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.766611] ACPI: Sleep Button [SLPB]
[    0.766650] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.766653] ACPI: Power Button [PWRF]
[    0.766703] ACPI: acpi_idle registered with cpuidle
[    0.766758] ACPI: processor limited to max C-state 1
[    0.772751] ACPI Warning: For \_TZ_.THRM._PSL: Return Package has no elements (empty) (20110413/nspredef-457)
[    0.772759] ACPI: [Package] has zero elements (f7660b00)
[    0.772761] ACPI: Invalid passive threshold
[    0.773242] thermal LNXTHERM:00: registered as thermal_zone0
[    0.773246] ACPI: Thermal Zone [THRM] (38 C)
[    0.773287] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.773315] ERST: Table is not found!
[    0.773425] isapnp: Scanning for PnP cards...
[    0.773434] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.809059] ACPI: Battery Slot [BAT0] (battery present)
[    1.153836] isapnp: No Plug & Play device found
[    1.163665] Linux agpgart interface v0.103
[    1.165115] brd: module loaded
[    1.165645] loop: module loaded
[    1.166104] Fixed MDIO Bus: probed
[    1.166126] PPP generic driver version 2.4.2
[    1.166168] tun: Universal TUN/TAP device driver, 1.6
[    1.166170] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.166246] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.166299] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.166317] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.166350] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.166364] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.166379] QUIRK: Enable AMD PLL fix
[    1.166390] ehci_hcd 0000:00:12.2: debug port 1
[    1.166414] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfeb08000
[    1.176113] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.176265] hub 1-0:1.0: USB hub found
[    1.176269] hub 1-0:1.0: 5 ports detected
[    1.176354] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.176372] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.176406] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.176421] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.176442] ehci_hcd 0000:00:13.2: debug port 1
[    1.176456] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfeb06000
[    1.188112] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.188265] hub 2-0:1.0: USB hub found
[    1.188269] hub 2-0:1.0: 5 ports detected
[    1.188349] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.188367] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.188406] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.188417] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.188438] ehci_hcd 0000:00:16.2: debug port 1
[    1.188453] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfeb04000
[    1.200112] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.200255] hub 3-0:1.0: USB hub found
[    1.200259] hub 3-0:1.0: 4 ports detected
[    1.200335] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.200355] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.200373] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.200407] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.200439] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfeb09000
[    1.260263] hub 4-0:1.0: USB hub found
[    1.260274] hub 4-0:1.0: 5 ports detected
[    1.260349] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.260366] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.260407] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.260429] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfeb07000
[    1.320234] hub 5-0:1.0: USB hub found
[    1.320245] hub 5-0:1.0: 5 ports detected
[    1.320319] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.320338] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.320372] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 6
[    1.320395] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfeb05000
[    1.380238] hub 6-0:1.0: USB hub found
[    1.380249] hub 6-0:1.0: 4 ports detected
[    1.380323] uhci_hcd: USB Universal Host Controller Interface driver
[    1.380407] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.382935] i8042: Detected active multiplexing controller, rev 1.1
[    1.384407] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.384413] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.384437] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.384459] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.384480] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.384575] mousedev: PS/2 mouse device common for all mice
[    1.384764] rtc_cmos 00:05: RTC can wake from S4
[    1.384852] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.384875] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.384956] device-mapper: uevent: version 1.0.3
[    1.385025] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.385053] EISA: Probing bus 0 at eisa.0
[    1.385055] EISA: Cannot allocate resource for mainboard
[    1.385057] Cannot allocate resource for EISA slot 1
[    1.385059] Cannot allocate resource for EISA slot 2
[    1.385061] Cannot allocate resource for EISA slot 3
[    1.385063] Cannot allocate resource for EISA slot 4
[    1.385065] Cannot allocate resource for EISA slot 5
[    1.385066] Cannot allocate resource for EISA slot 6
[    1.385068] Cannot allocate resource for EISA slot 7
[    1.385070] Cannot allocate resource for EISA slot 8
[    1.385072] EISA: Detected 0 cards.
[    1.385116] cpufreq-nforce2: No nForce2 chipset.
[    1.385118] cpuidle: using governor ladder
[    1.385120] cpuidle: using governor menu
[    1.385122] EFI Variables Facility v0.08 2004-May-17
[    1.385374] TCP cubic registered
[    1.385500] NET: Registered protocol family 10
[    1.386039] NET: Registered protocol family 17
[    1.386054] Registering the dns_resolver key type
[    1.386071] Using IPI No-Shortcut mode
[    1.386139] PM: Hibernation image not present or could not be loaded.
[    1.386150] registered taskstats version 1
[    1.399581]   Magic number: 7:369:150
[    1.399599] bdi 1:2: hash matches
[    1.399627] pci 0000:00:14.3: hash matches
[    1.399732] rtc_cmos 00:05: setting system clock to 2011-12-11 23:08:46 UTC (1323644926)
[    1.399744] powernow-k8: Found 1 AMD Phenom(tm) II N830 Triple-Core Processor (3 cpu cores) (version 2.20.00)
[    1.399782] powernow-k8:    0 : pstate 0 (2100 MHz)
[    1.399784] powernow-k8:    1 : pstate 1 (1800 MHz)
[    1.399786] powernow-k8:    2 : pstate 2 (1500 MHz)
[    1.399788] powernow-k8:    3 : pstate 3 (1200 MHz)
[    1.399790] powernow-k8:    4 : pstate 4 (800 MHz)
[    1.400067] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.400071] EDD information not available.
[    1.400296] Freeing unused kernel memory: 720k freed
[    1.400559] Write protecting the kernel text: 5500k
[    1.400630] Write protecting the kernel read-only data: 2240k
[    1.400632] NX-protecting the kernel data: 4740k
[    1.422114] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.423016] udevd[85]: starting version 173
[    1.455293] ahci 0000:00:11.0: version 3.0
[    1.455320] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.455369] ahci 0000:00:11.0: irq 43 for MSI/MSI-X
[    1.455455] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.455459] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.456296] scsi0 : ahci
[    1.458208] scsi1 : ahci
[    1.460571] scsi2 : ahci
[    1.461293] scsi3 : ahci
[    1.461367] ata1: SATA max UDMA/133 abar m1024@0xfeb0a000 port 0xfeb0a100 irq 43
[    1.461372] ata2: SATA max UDMA/133 abar m1024@0xfeb0a000 port 0xfeb0a180 irq 43
[    1.461375] ata3: SATA max UDMA/133 abar m1024@0xfeb0a000 port 0xfeb0a200 irq 43
[    1.461379] ata4: SATA max UDMA/133 abar m1024@0xfeb0a000 port 0xfeb0a280 irq 43
[    1.466442] sdhci: Secure Digital Host Controller Interface driver
[    1.466446] sdhci: Copyright(c) Pierre Ossman
[    1.468593] sdhci-pci 0000:05:00.0: SDHCI controller found [197b:2382] (rev 80)
[    1.468611] sdhci-pci 0000:05:00.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.468649] sdhci-pci 0000:05:00.0: setting latency timer to 64
[    1.468660] mmc0: no vmmc regulator found
[    1.468688] Registered led device: mmc0::
[    1.468725] mmc0: SDHCI controller on PCI [0000:05:00.0] using ADMA
[    1.468733] sdhci-pci 0000:05:00.2: SDHCI controller found [197b:2381] (rev 80)
[    1.468742] sdhci-pci 0000:05:00.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.468749] sdhci-pci 0000:05:00.2: Refusing to bind to secondary interface.
[    1.468789] sdhci-pci 0000:05:00.2: PCI INT B disabled
[    1.474495] jme: JMicron JMC2XX ethernet driver version 1.0.8
[    1.474530] jme 0000:05:00.5: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.474542] jme 0000:05:00.5: setting latency timer to 64
[    1.475608] jme 0000:05:00.5: eth0: JMC250 Gigabit Ethernet chiprev:23 pcirev:3 macaddr:bc:ae:c5:64:7f:ab
[    1.664122] usb 2-2: new high speed USB device number 2 using ehci_hcd
[    1.720117] Refined TSC clocksource calibration: 2094.754 MHz.
[    1.720124] Switching to clocksource tsc
[    1.780146] ata3: SATA link down (SStatus 0 SControl 300)
[    1.784124] ata4: SATA link down (SStatus 0 SControl 300)
[    1.952109] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.952136] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.954726] ata2.00: ATAPI: HL-DT-STDVDRAM GT34N, AS00, max UDMA/100
[    1.957640] ata2.00: configured for UDMA/100
[    1.958439] ata1.00: ATA-8: SAMSUNG HN-M101MBB, 2AR10001, max UDMA/133
[    1.958444] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.964786] ata1.00: configured for UDMA/133
[    1.964998] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HN-M101M 2AR1 PQ: 0 ANSI: 5
[    1.965193] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.965197] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.965236] sd 0:0:0:0: [sda] Write Protect is off
[    1.965239] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.965263] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.967733] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT34N     AS00 PQ: 0 ANSI: 5
[    1.972025] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.972030] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.972181] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.972258] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.013604]  sda: sda1 sda2 sda3 < sda5 >
[    2.013938] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.092105] usb 4-1: new full speed USB device number 2 using ohci_hcd
[    2.515178] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.524110] usb 4-2: new low speed USB device number 3 using ohci_hcd
[   14.929054] udevd[377]: starting version 173
[   14.990454] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   14.990740] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   14.990840] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[   14.992673] Adding 1998844k swap on /dev/sda5.  Priority:-1 extents:1 across:1998844k 
[   14.995593] lp: driver loaded but no devices found
[   15.012985] cfg80211: Calling CRDA to update world regulatory domain
[   15.013321] [drm] Initialized drm 1.1.0 20060810
[   15.014328] type=1400 audit(1323644940.108:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=499 comm="apparmor_parser"
[   15.014784] type=1400 audit(1323644940.108:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=499 comm="apparmor_parser"
[   15.015081] type=1400 audit(1323644940.108:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=499 comm="apparmor_parser"
[   15.017391] jmb38x_ms 0000:05:00.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   15.017399] jmb38x_ms 0000:05:00.3: setting latency timer to 64
[   15.062933] Bluetooth: Core ver 2.16
[   15.062980] NET: Registered protocol family 31
[   15.062982] Bluetooth: HCI device and connection manager initialized
[   15.062985] Bluetooth: HCI socket layer initialized
[   15.062987] Bluetooth: L2CAP socket layer initialized
[   15.063434] Bluetooth: SCO socket layer initialized
[   15.063796] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   15.067001] usbcore: registered new interface driver btusb
[   15.069652] [drm] radeon defaulting to kernel modesetting.
[   15.069656] [drm] radeon kernel modesetting enabled.
[   15.069731] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.069737] radeon 0000:01:00.0: setting latency timer to 64
[   15.070103] asus_laptop: Asus Laptop Support version 0.42
[   15.070245] asus_laptop: BSTS called, 0xfdff returned
[   15.072490] [drm] initializing kernel modesetting (CEDAR 0x1002:0x68E0 0x1043:0x1BF2).
[   15.072536] [drm] register mmio base: 0xFDF20000
[   15.072538] [drm] register mmio size: 131072
[   15.072717] ATOM BIOS: Asus
[   15.072789] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   15.072793] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   15.073040] [drm] Detected VRAM RAM=512M, BAR=256M
[   15.073045] [drm] RAM width 64bits DDR
[   15.081019] [TTM] Zone  kernel: Available graphics memory: 419108 kiB.
[   15.081022] [TTM] Zone highmem: Available graphics memory: 2058642 kiB.
[   15.081025] [TTM] Initializing pool allocator.
[   15.081047] [drm] radeon: 512M of VRAM memory ready
[   15.081049] [drm] radeon: 512M of GTT memory ready.
[   15.081064] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.081066] [drm] Driver supports precise vblank timestamp query.
[   15.081108] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[   15.081114] radeon 0000:01:00.0: radeon: using MSI.
[   15.081148] [drm] radeon: irq initialized.
[   15.081154] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   15.082684] [drm] Loading CEDAR Microcode
[   15.083827] ath9k 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.083838] ath9k 0000:04:00.0: setting latency timer to 64
[   15.132902] ath: EEPROM regdomain: 0x60
[   15.132904] ath: EEPROM indicates we should expect a direct regpair map
[   15.132907] ath: Country alpha2 being used: 00
[   15.132909] ath: Regpair used: 0x60
[   15.132916] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.132919] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132922] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.132925] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132927] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.132930] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132932] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.132935] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132937] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.132940] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132942] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.132945] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132947] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.132950] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132953] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.132955] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132958] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.132960] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132963] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.132966] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132968] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.132971] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132973] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.132976] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132978] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.132981] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.132983] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   15.132986] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   15.134376] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   15.137280] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.137913] Registered led device: ath9k-phy0
[   15.137922] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8660000, irq=16
[   15.144248] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.170785] asus_laptop: Backlight controlled by ACPI video driver
[   15.171105] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input5
[   15.195557] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   15.195621] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   15.228062] ACPI Warning: _BQC returned an invalid level (20110413/video-473)
[   15.257753] acpi device:40: registered as cooling_device3
[   15.260097] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:3d/LNXVIDEO:00/input/input8
[   15.260160] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.274618] Linux video capture interface: v2.00
[   15.275434] uvcvideo: Found UVC 1.00 device USB2.0 0.3M UVC WebCam (04f2:b1e5)
[   15.282784] input: 2.4G Receiver as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input9
[   15.282890] generic-usb 0003:1D57:32DA.0001: input,hidraw0: USB HID v1.10 Keyboard [2.4G Receiver] on usb-0000:00:12.0-2/input0
[   15.286875] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.289677] input: USB2.0 0.3M UVC WebCam as /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input11
[   15.290031] input: 2.4G Receiver as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input10
[   15.290131] generic-usb 0003:1D57:32DA.0002: input,hidraw1: USB HID v1.10 Mouse [2.4G Receiver] on usb-0000:00:12.0-2/input1
[   15.290202] usbcore: registered new interface driver uvcvideo
[   15.290205] USB Video Class driver (v1.1.0)
[   15.298425] input: 2.4G Receiver as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.2/input/input12
[   15.298577] generic-usb 0003:1D57:32DA.0003: input,hidraw2: USB HID v1.10 Device [2.4G Receiver] on usb-0000:00:12.0-2/input2
[   15.298615] usbcore: registered new interface driver usbhid
[   15.298617] usbhid: USB HID core driver
[   15.324255] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   15.324259] cfg80211: World regulatory domain updated:
[   15.324261] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.324265] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.324268] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.324271] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.324273] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.324276] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.362443] radeon 0000:01:00.0: WB enabled
[   15.378774] [drm] ring test succeeded in 0 usecs
[   15.378905] [drm] radeon: ib pool ready.
[   15.378972] [drm] ib test succeeded in 0 usecs
[   15.379283] [drm] Radeon Display Connectors
[   15.379285] [drm] Connector 0:
[   15.379286] [drm]   LVDS
[   15.379289] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[   15.379291] [drm]   Encoders:
[   15.379292] [drm]     LCD1: INTERNAL_UNIPHY
[   15.379294] [drm] Connector 1:
[   15.379295] [drm]   HDMI-A
[   15.379296] [drm]   HPD1
[   15.379298] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[   15.379300] [drm]   Encoders:
[   15.379302] [drm]     DFP1: INTERNAL_UNIPHY1
[   15.379303] [drm] Connector 2:
[   15.379305] [drm]   VGA
[   15.379307] [drm]   DDC: 0x64d8 0x64d8 0x64dc 0x64dc 0x64e0 0x64e0 0x64e4 0x64e4
[   15.379309] [drm]   Encoders:
[   15.379310] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.389358] [drm] Radeon display connector LVDS-1: No monitor connected or invalid EDID
[   15.399357] [drm] Radeon display connector HDMI-A-1: No monitor connected or invalid EDID
[   15.409274] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
[   15.409305] [drm] Internal thermal controller without fan control
[   15.409359] [drm] radeon: power management initialized
[   15.499437] elantech: assuming hardware version 2, firmware version 4.1.2
[   15.534668] elantech: Synaptics capabilities query result 0x78, 0x16, 0x0d.
[   15.633087] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input13
[   15.832146] [drm] fb mappable at 0xD0141000
[   15.832150] [drm] vram apper at 0xD0000000
[   15.832152] [drm] size 4325376
[   15.832153] [drm] fb depth is 24
[   15.832155] [drm]    pitch is 5632
[   15.832248] fbcon: radeondrmfb (fb0) is primary device
[   15.832354] Console: switching to colour frame buffer device 170x48
[   15.832389] fb0: radeondrmfb frame buffer device
[   15.832391] drm: registered panic notifier
[   15.832398] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:00.0 on minor 0
[   15.832473] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.832549] HDA Intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   15.832574] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.859372] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   15.859497] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
[   16.004419] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   16.561132] ppdev: user-space parallel port driver
[   16.570285] type=1400 audit(1323644941.664:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1029 comm="apparmor_parser"
[   16.570815] type=1400 audit(1323644941.664:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1029 comm="apparmor_parser"
[   16.699871] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.705726] jme 0000:05:00.5: irq 46 for MSI/MSI-X
[   16.706293] jme 0000:05:00.5: eth0: Link is down
[   16.706549] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.714268] type=1400 audit(1323644941.808:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1045 comm="apparmor_parser"
[   16.714911] type=1400 audit(1323644941.808:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1045 comm="apparmor_parser"
[   16.715159] type=1400 audit(1323644941.808:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1045 comm="apparmor_parser"
[   16.717785] type=1400 audit(1323644941.812:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1046 comm="apparmor_parser"
[   16.721090] type=1400 audit(1323644941.816:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1048 comm="apparmor_parser"
[   16.811701] init: failsafe main process (964) killed by TERM signal
[   16.813788] init: apport pre-start process (1081) terminated with status 1

---

### Post by anforguiven on 2011-12-11
> **guillermolisi said:**
> Para empezar, mostranos la salida de los siguientes comandos ```
sudo lshw
``` ```
lspci
``` y el contenido de /var/log/dmesg y /var/log/Xorg.0.log (que son generalmente largo). Todo esto usando una consola/terminal.

Por lo que comentas pareceria ser problemas con ACPI y la administracion de energia.

/var/log/Xorg.0.log
[    16.877] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    16.877] X Protocol Version 11, Revision 0
[    16.877] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    16.877] Current Operating System: Linux ASUS 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686
[    16.877] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic-pae root=UUID=e6ef367d-4ddc-4d9e-a1ce-ae8b2a3d52ae ro quiet splash vt.handoff=7
[    16.877] Build Date: 19 October 2011  05:09:41AM
[    16.877] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    16.877] Current version of pixman: 0.22.2
[    16.877] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    16.877] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.877] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 11 20:09:01 2011
[    16.901] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.901] (==) No Layout section.  Using the first Screen section.
[    16.901] (==) No screen section available. Using defaults.
[    16.902] (**) |-->Screen "Default Screen Section" (0)
[    16.902] (**) |   |-->Monitor "<default monitor>"
[    16.902] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    16.902] (==) Automatically adding devices
[    16.902] (==) Automatically enabling devices
[    16.902] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.902] 	Entry deleted from font path.
[    16.902] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.902] 	Entry deleted from font path.
[    16.902] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.902] 	Entry deleted from font path.
[    16.902] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.902] 	Entry deleted from font path.
[    16.902] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.902] 	Entry deleted from font path.
[    16.902] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    16.902] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.902] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.902] (II) Loader magic: 0x823ada0
[    16.902] (II) Module ABI versions:
[    16.902] 	X.Org ANSI C Emulation: 0.4
[    16.902] 	X.Org Video Driver: 10.0
[    16.902] 	X.Org XInput driver : 12.3
[    16.902] 	X.Org Server Extension : 5.0
[    16.903] (--) PCI:*(0:1:0:0) 1002:68e0:1043:1bf2 rev 0, Mem @ 0xd0000000/268435456, 0xfdf20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    16.903] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.903] (II) LoadModule: "extmod"
[    16.928] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.928] (II) Module extmod: vendor="X.Org Foundation"
[    16.928] 	compiled for 1.10.4, module version = 1.0.0
[    16.928] 	Module class: X.Org Server Extension
[    16.928] 	ABI class: X.Org Server Extension, version 5.0
[    16.928] (II) Loading extension MIT-SCREEN-SAVER
[    16.928] (II) Loading extension XFree86-VidModeExtension
[    16.928] (II) Loading extension XFree86-DGA
[    16.928] (II) Loading extension DPMS
[    16.928] (II) Loading extension XVideo
[    16.928] (II) Loading extension XVideo-MotionCompensation
[    16.928] (II) Loading extension X-Resource
[    16.928] (II) LoadModule: "dbe"
[    16.928] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.928] (II) Module dbe: vendor="X.Org Foundation"
[    16.928] 	compiled for 1.10.4, module version = 1.0.0
[    16.928] 	Module class: X.Org Server Extension
[    16.928] 	ABI class: X.Org Server Extension, version 5.0
[    16.928] (II) Loading extension DOUBLE-BUFFER
[    16.928] (II) LoadModule: "glx"
[    16.928] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.928] (II) Module glx: vendor="X.Org Foundation"
[    16.928] 	compiled for 1.10.4, module version = 1.0.0
[    16.928] 	ABI class: X.Org Server Extension, version 5.0
[    16.928] (==) AIGLX enabled
[    16.928] (II) Loading extension GLX
[    16.928] (II) LoadModule: "record"
[    16.929] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.929] (II) Module record: vendor="X.Org Foundation"
[    16.929] 	compiled for 1.10.4, module version = 1.13.0
[    16.929] 	Module class: X.Org Server Extension
[    16.929] 	ABI class: X.Org Server Extension, version 5.0
[    16.929] (II) Loading extension RECORD
[    16.929] (II) LoadModule: "dri"
[    16.929] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.929] (II) Module dri: vendor="X.Org Foundation"
[    16.929] 	compiled for 1.10.4, module version = 1.0.0
[    16.929] 	ABI class: X.Org Server Extension, version 5.0
[    16.929] (II) Loading extension XFree86-DRI
[    16.929] (II) LoadModule: "dri2"
[    16.929] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.929] (II) Module dri2: vendor="X.Org Foundation"
[    16.929] 	compiled for 1.10.4, module version = 1.2.0
[    16.929] 	ABI class: X.Org Server Extension, version 5.0
[    16.929] (II) Loading extension DRI2
[    16.929] (==) Matched fglrx as autoconfigured driver 0
[    16.929] (==) Matched ati as autoconfigured driver 1
[    16.929] (==) Matched vesa as autoconfigured driver 2
[    16.929] (==) Matched fbdev as autoconfigured driver 3
[    16.929] (==) Assigned the driver to the xf86ConfigLayout
[    16.929] (II) LoadModule: "fglrx"
[    16.950] (WW) Warning, couldn't open module fglrx
[    16.950] (II) UnloadModule: "fglrx"
[    16.950] (II) Unloading fglrx
[    16.950] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    16.950] (II) LoadModule: "ati"
[    16.950] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    16.950] (II) Module ati: vendor="X.Org Foundation"
[    16.950] 	compiled for 1.10.2.902, module version = 6.14.99
[    16.950] 	Module class: X.Org Video Driver
[    16.950] 	ABI class: X.Org Video Driver, version 10.0
[    16.950] (II) LoadModule: "radeon"
[    16.951] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    16.951] (II) Module radeon: vendor="X.Org Foundation"
[    16.951] 	compiled for 1.10.2.902, module version = 6.14.99
[    16.951] 	Module class: X.Org Video Driver
[    16.951] 	ABI class: X.Org Video Driver, version 10.0
[    16.951] (II) LoadModule: "vesa"
[    16.951] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.951] (II) Module vesa: vendor="X.Org Foundation"
[    16.951] 	compiled for 1.10.2, module version = 2.3.0
[    16.951] 	Module class: X.Org Video Driver
[    16.951] 	ABI class: X.Org Video Driver, version 10.0
[    16.951] (II) LoadModule: "fbdev"
[    16.952] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.952] (II) Module fbdev: vendor="X.Org Foundation"
[    16.952] 	compiled for 1.10.0, module version = 0.4.2
[    16.952] 	ABI class: X.Org Video Driver, version 10.0
[    16.952] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS
[    16.955] (II) VESA: driver for VESA chipsets: vesa
[    16.955] (II) FBDEV: driver for framebuffer: fbdev
[    16.955] (++) using VT number 7

[    16.955] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    16.955] (II) [KMS] Kernel modesetting enabled.
[    16.955] (WW) Falling back to old probe method for vesa
[    16.955] (WW) Falling back to old probe method for fbdev
[    16.955] (II) Loading sub module "fbdevhw"
[    16.955] (II) LoadModule: "fbdevhw"
[    16.955] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.955] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.955] 	compiled for 1.10.4, module version = 0.0.2
[    16.955] 	ABI class: X.Org Video Driver, version 10.0
[    16.955] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    16.955] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    16.955] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    16.955] (==) RADEON(0): Default visual is TrueColor
[    16.955] (==) RADEON(0): RGB weight 888
[    16.955] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    16.955] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 5000 Series" (ChipID = 0x68e0)
[    16.956] (II) RADEON(0): PCIE card detected
[    16.956] drmOpenDevice: node name is /dev/dri/card0
[    16.956] drmOpenDevice: open result is 12, (OK)
[    16.956] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    16.956] drmOpenDevice: node name is /dev/dri/card0
[    16.956] drmOpenDevice: open result is 12, (OK)
[    16.956] drmOpenByBusid: drmOpenMinor returns 12
[    16.956] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    16.956] (II) Loading sub module "exa"
[    16.956] (II) LoadModule: "exa"
[    16.956] (II) Loading /usr/lib/xorg/modules/libexa.so
[    16.956] (II) Module exa: vendor="X.Org Foundation"
[    16.956] 	compiled for 1.10.4, module version = 2.5.0
[    16.956] 	ABI class: X.Org Video Driver, version 10.0
[    16.956] (II) RADEON(0): KMS Color Tiling: enabled
[    16.956] (II) RADEON(0): KMS Pageflipping: enabled
[    16.956] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    16.976] (II) RADEON(0): Output LVDS has no monitor section
[    16.981] (II) RADEON(0): Output HDMI-0 has no monitor section
[    17.004] (II) RADEON(0): Output VGA-0 has no monitor section
[    17.025] (II) RADEON(0): EDID for output LVDS
[    17.025] (II) RADEON(0): Printing probed modes for output LVDS
[    17.025] (II) RADEON(0): Modeline "1366x768"x60.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
[    17.025] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    17.025] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    17.025] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    17.025] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    17.025] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    17.025] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    17.025] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    17.029] (II) RADEON(0): EDID for output HDMI-0
[    17.056] (II) RADEON(0): EDID for output VGA-0
[    17.056] (II) RADEON(0): Output LVDS connected
[    17.056] (II) RADEON(0): Output HDMI-0 disconnected
[    17.056] (II) RADEON(0): Output VGA-0 disconnected
[    17.056] (II) RADEON(0): Using exact sizes for initial modes
[    17.056] (II) RADEON(0): Output LVDS using initial mode 1366x768
[    17.056] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.056] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:20000000 visible:fba0000
[    17.056] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    17.056] (==) RADEON(0): DPI set to (96, 96)
[    17.056] (II) Loading sub module "fb"
[    17.056] (II) LoadModule: "fb"
[    17.056] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.056] (II) Module fb: vendor="X.Org Foundation"
[    17.057] 	compiled for 1.10.4, module version = 1.0.0
[    17.057] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.057] (II) Loading sub module "ramdac"
[    17.057] (II) LoadModule: "ramdac"
[    17.057] (II) Module "ramdac" already built-in
[    17.057] (II) UnloadModule: "vesa"
[    17.057] (II) Unloading vesa
[    17.057] (II) UnloadModule: "fbdev"
[    17.057] (II) Unloading fbdev
[    17.057] (II) UnloadModule: "fbdevhw"
[    17.057] (II) Unloading fbdevhw
[    17.057] (--) Depth 24 pixmap format is 32 bpp
[    17.057] (II) RADEON(0): [DRI2] Setup complete
[    17.057] (II) RADEON(0): [DRI2]   DRI driver: r600
[    17.057] (II) RADEON(0): Front buffer size: 4224K
[    17.057] (II) RADEON(0): VRAM usage limit set to 228096K
[    17.057] (==) RADEON(0): Backing store disabled
[    17.057] (II) RADEON(0): Direct rendering enabled
[    17.057] (II) RADEON(0): Setting EXA maxPitchBytes
[    17.057] (II) EXA(0): Driver allocated offscreen pixmaps
[    17.057] (II) EXA(0): Driver registered support for the following operations:
[    17.057] (II)         Solid
[    17.057] (II)         Copy
[    17.057] (II)         Composite (RENDER acceleration)
[    17.057] (II)         UploadToScreen
[    17.057] (II)         DownloadFromScreen
[    17.057] (II) RADEON(0): Acceleration enabled
[    17.057] (==) RADEON(0): DPMS enabled
[    17.057] (==) RADEON(0): Silken mouse enabled
[    17.057] (II) RADEON(0): Set up textured video
[    17.057] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    17.057] (II) RADEON(0): [XvMC] Extension initialized.
[    17.057] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.057] (--) RandR disabled
[    17.057] (II) Initializing built-in extension Generic Event Extension
[    17.057] (II) Initializing built-in extension SHAPE
[    17.057] (II) Initializing built-in extension MIT-SHM
[    17.057] (II) Initializing built-in extension XInputExtension
[    17.057] (II) Initializing built-in extension XTEST
[    17.057] (II) Initializing built-in extension BIG-REQUESTS
[    17.057] (II) Initializing built-in extension SYNC
[    17.057] (II) Initializing built-in extension XKEYBOARD
[    17.057] (II) Initializing built-in extension XC-MISC
[    17.057] (II) Initializing built-in extension SECURITY
[    17.057] (II) Initializing built-in extension XINERAMA
[    17.057] (II) Initializing built-in extension XFIXES
[    17.057] (II) Initializing built-in extension RENDER
[    17.057] (II) Initializing built-in extension RANDR
[    17.057] (II) Initializing built-in extension COMPOSITE
[    17.057] (II) Initializing built-in extension DAMAGE
[    17.057] (II) Initializing built-in extension GESTURE
[    17.067] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/r600_dri.so
[    17.078] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    17.078] (II) AIGLX: enabled GLX_INTEL_swap_event
[    17.078] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    17.078] (II) AIGLX: enabled GLX_SGI_make_current_read
[    17.078] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    17.078] (II) AIGLX: Loaded and initialized r600
[    17.078] (II) GLX: Initialized DRI2 GL provider for screen 0
[    17.079] (II) RADEON(0): Setting screen physical size to 361 x 203
[    17.089] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.099] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    17.099] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.099] (II) LoadModule: "evdev"
[    17.099] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.100] (II) Module evdev: vendor="X.Org Foundation"
[    17.100] 	compiled for 1.10.2, module version = 2.6.0
[    17.100] 	Module class: X.Org XInput Driver
[    17.100] 	ABI class: X.Org XInput driver, version 12.3
[    17.100] (II) Using input driver 'evdev' for 'Power Button'
[    17.100] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.100] (**) Power Button: always reports core events
[    17.100] (**) Power Button: Device: "/dev/input/event3"
[    17.100] (--) Power Button: Found keys
[    17.100] (II) Power Button: Configuring as keyboard
[    17.100] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    17.100] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.100] (**) Option "xkb_rules" "evdev"
[    17.100] (**) Option "xkb_model" "pc105"
[    17.100] (**) Option "xkb_layout" "es"
[    17.103] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    17.113] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    17.113] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    17.113] (II) Using input driver 'evdev' for 'Video Bus'
[    17.113] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.113] (**) Video Bus: always reports core events
[    17.113] (**) Video Bus: Device: "/dev/input/event8"
[    17.113] (--) Video Bus: Found keys
[    17.113] (II) Video Bus: Configuring as keyboard
[    17.113] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:3d/LNXVIDEO:00/input/input8/event8"
[    17.113] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    17.113] (**) Option "xkb_rules" "evdev"
[    17.114] (**) Option "xkb_model" "pc105"
[    17.114] (**) Option "xkb_layout" "es"
[    17.114] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    17.114] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.114] (II) Using input driver 'evdev' for 'Power Button'
[    17.114] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.114] (**) Power Button: always reports core events
[    17.114] (**) Power Button: Device: "/dev/input/event0"
[    17.115] (--) Power Button: Found keys
[    17.115] (II) Power Button: Configuring as keyboard
[    17.115] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    17.115] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.115] (**) Option "xkb_rules" "evdev"
[    17.115] (**) Option "xkb_model" "pc105"
[    17.115] (**) Option "xkb_layout" "es"
[    17.115] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    17.115] (II) No input driver/identifier specified (ignoring)
[    17.115] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    17.115] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    17.115] (II) Using input driver 'evdev' for 'Sleep Button'
[    17.115] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.115] (**) Sleep Button: always reports core events
[    17.115] (**) Sleep Button: Device: "/dev/input/event2"
[    17.116] (--) Sleep Button: Found keys
[    17.116] (II) Sleep Button: Configuring as keyboard
[    17.116] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    17.116] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    17.116] (**) Option "xkb_rules" "evdev"
[    17.116] (**) Option "xkb_model" "pc105"
[    17.116] (**) Option "xkb_layout" "es"
[    17.119] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event14)
[    17.119] (II) No input driver/identifier specified (ignoring)
[    17.123] (II) config/udev: Adding input device 2.4G Receiver (/dev/input/event9)
[    17.123] (**) 2.4G Receiver: Applying InputClass "evdev keyboard catchall"
[    17.123] (II) Using input driver 'evdev' for '2.4G Receiver'
[    17.123] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.123] (**) 2.4G Receiver: always reports core events
[    17.123] (**) 2.4G Receiver: Device: "/dev/input/event9"
[    17.123] (--) 2.4G Receiver: Found keys
[    17.123] (II) 2.4G Receiver: Configuring as keyboard
[    17.123] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input9/event9"
[    17.123] (II) XINPUT: Adding extended input device "2.4G Receiver" (type: KEYBOARD)
[    17.123] (**) Option "xkb_rules" "evdev"
[    17.123] (**) Option "xkb_model" "pc105"
[    17.123] (**) Option "xkb_layout" "es"
[    17.124] (II) config/udev: Adding input device 2.4G Receiver (/dev/input/event11)
[    17.124] (**) 2.4G Receiver: Applying InputClass "evdev pointer catchall"
[    17.124] (II) Using input driver 'evdev' for '2.4G Receiver'
[    17.124] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.124] (**) 2.4G Receiver: always reports core events
[    17.124] (**) 2.4G Receiver: Device: "/dev/input/event11"
[    17.124] (--) 2.4G Receiver: Found 9 mouse buttons
[    17.124] (--) 2.4G Receiver: Found scroll wheel(s)
[    17.124] (--) 2.4G Receiver: Found relative axes
[    17.124] (--) 2.4G Receiver: Found x and y relative axes
[    17.124] (II) 2.4G Receiver: Configuring as mouse
[    17.124] (II) 2.4G Receiver: Adding scrollwheel support
[    17.124] (**) 2.4G Receiver: YAxisMapping: buttons 4 and 5
[    17.124] (**) 2.4G Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.124] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input10/event11"
[    17.124] (II) XINPUT: Adding extended input device "2.4G Receiver" (type: MOUSE)
[    17.124] (II) 2.4G Receiver: initialized for relative axes.
[    17.124] (**) 2.4G Receiver: (accel) keeping acceleration scheme 1
[    17.124] (**) 2.4G Receiver: (accel) acceleration profile 0
[    17.124] (**) 2.4G Receiver: (accel) acceleration factor: 2.000
[    17.124] (**) 2.4G Receiver: (accel) acceleration threshold: 4
[    17.124] (II) config/udev: Adding input device 2.4G Receiver (/dev/input/mouse0)
[    17.124] (II) No input driver/identifier specified (ignoring)
[    17.125] (II) config/udev: Adding input device 2.4G Receiver (/dev/input/event12)
[    17.125] (**) 2.4G Receiver: Applying InputClass "evdev keyboard catchall"
[    17.125] (II) Using input driver 'evdev' for '2.4G Receiver'
[    17.125] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.125] (**) 2.4G Receiver: always reports core events
[    17.125] (**) 2.4G Receiver: Device: "/dev/input/event12"
[    17.125] (--) 2.4G Receiver: Found 1 mouse buttons
[    17.125] (--) 2.4G Receiver: Found scroll wheel(s)
[    17.125] (--) 2.4G Receiver: Found relative axes
[    17.125] (--) 2.4G Receiver: Found absolute axes
[    17.125] (II) evdev-grail: failed to open grail, no gesture support
[    17.125] (--) 2.4G Receiver: Found keys
[    17.125] (II) 2.4G Receiver: Configuring as mouse
[    17.125] (II) 2.4G Receiver: Configuring as keyboard
[    17.125] (II) 2.4G Receiver: Adding scrollwheel support
[    17.125] (**) 2.4G Receiver: YAxisMapping: buttons 4 and 5
[    17.125] (**) 2.4G Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.125] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.2/input/input12/event12"
[    17.125] (II) XINPUT: Adding extended input device "2.4G Receiver" (type: KEYBOARD)
[    17.125] (**) Option "xkb_rules" "evdev"
[    17.125] (**) Option "xkb_model" "pc105"
[    17.125] (**) Option "xkb_layout" "es"
[    17.125] (EE) 2.4G Receiver: failed to initialize for relative axes.
[    17.125] (II) 2.4G Receiver: initialized for absolute axes.
[    17.126] (**) 2.4G Receiver: (accel) keeping acceleration scheme 1
[    17.126] (**) 2.4G Receiver: (accel) acceleration profile 0
[    17.126] (**) 2.4G Receiver: (accel) acceleration factor: 2.000
[    17.126] (**) 2.4G Receiver: (accel) acceleration threshold: 4
[    17.127] (II) config/udev: Adding input device USB2.0 0.3M UVC WebCam (/dev/input/event10)
[    17.127] (**) USB2.0 0.3M UVC WebCam: Applying InputClass "evdev keyboard catchall"
[    17.127] (II) Using input driver 'evdev' for 'USB2.0 0.3M UVC WebCam'
[    17.127] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.127] (**) USB2.0 0.3M UVC WebCam: always reports core events
[    17.127] (**) USB2.0 0.3M UVC WebCam: Device: "/dev/input/event10"
[    17.127] (--) USB2.0 0.3M UVC WebCam: Found keys
[    17.127] (II) USB2.0 0.3M UVC WebCam: Configuring as keyboard
[    17.127] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input11/event10"
[    17.127] (II) XINPUT: Adding extended input device "USB2.0 0.3M UVC WebCam" (type: KEYBOARD)
[    17.127] (**) Option "xkb_rules" "evdev"
[    17.127] (**) Option "xkb_model" "pc105"
[    17.127] (**) Option "xkb_layout" "es"
[    17.128] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event6)
[    17.128] (II) No input driver/identifier specified (ignoring)
[    17.128] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event7)
[    17.128] (II) No input driver/identifier specified (ignoring)
[    17.130] (II) config/udev: Adding input device Asus Laptop extra buttons (/dev/input/event5)
[    17.130] (**) Asus Laptop extra buttons: Applying InputClass "evdev keyboard catchall"
[    17.130] (II) Using input driver 'evdev' for 'Asus Laptop extra buttons'
[    17.130] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.130] (**) Asus Laptop extra buttons: always reports core events
[    17.130] (**) Asus Laptop extra buttons: Device: "/dev/input/event5"
[    17.130] (--) Asus Laptop extra buttons: Found keys
[    17.130] (II) Asus Laptop extra buttons: Configuring as keyboard
[    17.130] (**) Option "config_info" "udev:/sys/devices/platform/asus_laptop/input/input5/event5"
[    17.130] (II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD)
[    17.130] (**) Option "xkb_rules" "evdev"
[    17.130] (**) Option "xkb_model" "pc105"
[    17.130] (**) Option "xkb_layout" "es"
[    17.130] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    17.131] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    17.131] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    17.131] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.131] (**) AT Translated Set 2 keyboard: always reports core events
[    17.131] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    17.131] (--) AT Translated Set 2 keyboard: Found keys
[    17.131] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    17.131] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    17.131] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    17.131] (**) Option "xkb_rules" "evdev"
[    17.131] (**) Option "xkb_model" "pc105"
[    17.131] (**) Option "xkb_layout" "es"
[    17.131] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event13)
[    17.131] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    17.131] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    17.131] (II) LoadModule: "synaptics"
[    17.132] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    17.132] (II) Module synaptics: vendor="X.Org Foundation"
[    17.132] 	compiled for 1.10.4, module version = 1.4.1
[    17.132] 	Module class: X.Org XInput Driver
[    17.132] 	ABI class: X.Org XInput driver, version 12.3
[    17.132] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    17.132] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    17.132] (**) ETPS/2 Elantech Touchpad: always reports core events
[    17.132] (**) Option "Device" "/dev/input/event13"
[    17.176] (--) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[    17.176] (--) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
[    17.176] (--) ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    17.176] (--) ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    17.176] (--) ETPS/2 Elantech Touchpad: buttons: left right double triple
[    17.208] (--) ETPS/2 Elantech Touchpad: touchpad found
[    17.208] (**) ETPS/2 Elantech Touchpad: always reports core events
[    17.284] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input13/event13"
[    17.284] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[    17.284] (**) ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    17.284] (**) ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    17.284] (**) ETPS/2 Elantech Touchpad: AccelFactor is now 0.147
[    17.284] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    17.284] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    17.284] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    17.284] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    17.285] (--) ETPS/2 Elantech Touchpad: touchpad found
[    17.285] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    17.285] (II) No input driver/identifier specified (ignoring)
[    22.239] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm

---

### Post by guillermolisi on 2011-12-11
El primer error o advertencia respecto de ACPI en el archivo /var/log/dmesg > [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignoredcorresponde a un bug que esta reportado en [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795099](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795099)

Como podras ver, como el bug involucra una funcionalidad del kernel Linux, fue marcado y asignado como correspondiente a linux-kernel-bugs. Es decir, los desarrolladores del kernel se encargaran de ver porque pasa esto con ese hardware.

Respecto del problema de la suspension del sistema, [aqui hay una solucion]("http://ubuntuforums.org/showpost.php?p=11516491&postcount=9") esto palia el problema que genera ACPI a traves de este error > 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)

En ese mismo thread estan viendo el tema de la hibernacion, asi que si lo seguis posiblemente tambien encuentres una forma de solucionar ese problema.

De todas formas y si no te es molestia y no tenes en la maquina contenido sensible que no podes perder, [probaria lo que sugieren en Phoronix]("http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=1") respecto de este problema recurrente sobre el correcto reconocimineto de las tablas ACPI por parte del kernel (como podras ver, la detallada nota es de Novimebre de este año y hay un link a una lista de hardware sobre el que se han reportado problemas como el tuyo).

En esa nota sugieren aplicar un [patch]("https://lkml.org/lkml/diff/2011/11/10/467/1"), parche, al kernel hasta que se desarrolle una solucion de fondo. A partir de la segunda pagina de la nota tenes cuadros informativos y detalle de como se comportaron los sistema probados antes y despues de la aplicacion de parche.

Como se aplica un patch ? [Aqui hay una explicacion]("http://www.mjmwired.net/kernel/Documentation/applying-patches.txt") (en Ingles)

Parece que sera posible una solucion "de fabrica" recien para la version 3.3 del kernel.

---

### Post by anforguiven on 2011-12-12
> **guillermolisi said:**
> El primer error o advertencia respecto de ACPI en el archivo /var/log/dmesg corresponde a un bug que esta reportado en [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795099](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795099)

Como podras ver, como el bug involucra una funcionalidad del kernel Linux, fue marcado y asignado como correspondiente a linux-kernel-bugs. Es decir, los desarrolladores del kernel se encargaran de ver porque pasa esto con ese hardware.

Respecto del problema de la suspension del sistema, [aqui hay una solucion]("http://ubuntuforums.org/showpost.php?p=11516491&postcount=9") esto palia el problema que genera ACPI a traves de este error 

En ese mismo thread estan viendo el tema de la hibernacion, asi que si lo seguis posiblemente tambien encuentres una forma de solucionar ese problema.

De todas formas y si no te es molestia y no tenes en la maquina contenido sensible que no podes perder, [probaria lo que sugieren en Phoronix]("http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=1") respecto de este problema recurrente sobre el correcto reconocimineto de las tablas ACPI por parte del kernel (como podras ver, la detallada nota es de Novimebre de este año y hay un link a una lista de hardware sobre el que se han reportado problemas como el tuyo).

En esa nota sugieren aplicar un [patch]("https://lkml.org/lkml/diff/2011/11/10/467/1"), parche, al kernel hasta que se desarrolle una solucion de fondo. A partir de la segunda pagina de la nota tenes cuadros informativos y detalle de como se comportaron los sistema probados antes y despues de la aplicacion de parche.

Como se aplica un patch ? [Aqui hay una explicacion]("http://www.mjmwired.net/kernel/Documentation/applying-patches.txt") (en Ingles)

Parece que sera posible una solucion "de fabrica" recien para la version 3.3 del kernel.

La suspencion logre arreglarla,el parche no logre instalarlo le dedique varias horas pero no logro entender como se hace, guarde el texto del parche con gedit y le puse como nombre diff y las letras se pusieron de colores. luego instale el programa patch y trate de seguir las instrucciones con mi limitado ingles con la consola como root pero lo unico que logro hacer es esto:


marcos@ASUS:~$ patch -p1 -i /home/marcos/diff
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/acpi/pci_root.c b/drivers/acpi/pci_root.c
|index 2672c79..7aff631 100644
|--- a/drivers/acpi/pci_root.c
|+++ b/drivers/acpi/pci_root.c
--------------------------
File to patch:


Es mas que evidente que esto tanteando no sale...

---

### Post by guillermolisi on 2011-12-13
Fijate que hay que reemplazar /a y /b por los paths en donde se encuentran los archivos que se mencionan en el patch > How do I apply or revert a patch?
31	---
32	 You apply a patch with the `patch' program. The patch program reads a diff
33	(or patch) file and makes the changes to the source tree described in it.
34	
35	Patches for the Linux kernel are generated relative to the parent directory
36	holding the kernel source dir.
37	
38	This means that paths to files inside the patch file contain the name of the
39	kernel source directories it was generated against (or some other directory
40	names like "a/" and "b/").
41	Since this is unlikely to match the name of the kernel source dir on your
42	local machine (but is often useful info to see what version an otherwise
43	unlabeled patch was generated against) you should change into your kernel
44	source directory and then strip the first element of the path from filenames
45	in the patch file when applying it (the -p1 argument to `patch' does this).
46	
47	To revert a previously applied patch, use the -R argument to patch.
48	So, if you applied a patch like this:
49		patch -p1 < ../patch-x.y.z

Para eso tenes que tener los fuentes del kernel y saber en donde esta el archivo a modificar (que podes ubicarlo con el comando "locate", por ejemplo).

---

### Post by anforguiven on 2011-12-13
> **guillermolisi said:**
> Fijate que hay que reemplazar /a y /b por los paths en donde se encuentran los archivos que se mencionan en el patch 

Para eso tenes que tener los fuentes del kernel y saber en donde esta el archivo a modificar (que podes ubicarlo con el comando "locate", por ejemplo).

Me doy por vencido no me sale!
Es frustrante al extremo!
Aparte de lo que me explicaste busque alternativas de como hacerlo pero no me sale! Un fracaso mi maquina con Ubuntu encima acá donde yo vivo a los "técnicos" le nombras Linux y te dicen ¿¿Que?? y después viene lo peor porque te dicen ¿¿por que no le pones XP?? jajaja.
Lo que mas lamento es hacerte perder tu tiempo.

---

### Post by anforguiven on 2011-12-14
> **guillermolisi said:**
> Fijate que hay que reemplazar /a y /b por los paths en donde se encuentran los archivos que se mencionan en el patch 

Para eso tenes que tener los fuentes del kernel y saber en donde esta el archivo a modificar (que podes ubicarlo con el comando "locate", por ejemplo).

Estoy bajando Ubuntu 10.04.3 x32 a ver si mejora o se resuelve este problema porque no quiero volver windows XD.

---

