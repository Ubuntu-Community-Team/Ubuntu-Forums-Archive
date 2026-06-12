---
title: "Usb mouse not recognized"
date: 2009-07-14
forum: Hardware
---

### Post by jutaymfm on 2009-07-14
Hi,
after updating HPLIP and ATI drivers (and all dependents packages), and booting my Toshiba Satellite_A215-S4767 notebook, when i plugin my optical usb mouse my system is not able to recognize it (in other hand, my touchpad still works, full-fuctional).
Some informarions

root@my-workstation:~# uname -a
Linux my-workstation 2.6.27-14-generic #1 SMP Tue Jul 7 22:18:38 UTC 2009 x86_64 GNU/Linux

root@my-workstation:~# lsusb
Bus 006 Device 004: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


root@my-workstation:~# cat /etc/modprobe.d/options 
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# Stop auto-association.
# LP: #264104
options ipw2200 associate=0

# XXX: Ignore HPA by default. Needs to be revisted in jaunty
options libata ignore_hpa=1



The error that I received from my syslog log file when i plugin my optical USB mouse is:

Jul 14 17:41:37 my-workstation kernel: [ 1702.924199] usb 4-1: new full speed USB device using ohci_hcd and address 31
Jul 14 17:41:37 my-workstation kernel: [ 1703.065207] usb 4-1: device descriptor read/64, error -62
Jul 14 17:41:37 my-workstation kernel: [ 1703.308078] usb 4-1: device descriptor read/64, error -62
Jul 14 17:41:37 my-workstation kernel: [ 1703.549054] usb 4-1: new full speed USB device using ohci_hcd and address 32
Jul 14 17:41:37 my-workstation kernel: [ 1703.689213] usb 4-1: device descriptor read/64, error -62
Jul 14 17:41:38 my-workstation kernel: [ 1703.933146] usb 4-1: device descriptor read/64, error -62
Jul 14 17:41:38 my-workstation kernel: [ 1704.173047] usb 4-1: new full speed USB device using ohci_hcd and address 33
Jul 14 17:41:38 my-workstation kernel: [ 1704.581046] usb 4-1: device not accepting address 33, error -62
Jul 14 17:41:38 my-workstation kernel: [ 1704.716109] usb 4-1: new full speed USB device using ohci_hcd and address 34
Jul 14 17:41:39 my-workstation kernel: [ 1705.125048] usb 4-1: device not accepting address 34, error -62
Jul 14 17:41:39 my-workstation kernel: [ 1705.125882] hub 4-0:1.0: unable to enumerate USB device on port 1



This is my lshw report:

root@my-workstation:~# lshw
my-workstation      
    description: Notebook
    product: Satellite A215
    vendor: TOSHIBA
    version: PSAEGU-00Y00V
    serial: 77210877K
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=oem-specific chassis=notebook uuid=33BD91D8-2680-11DC-8A10-001B3818D9D4
  *-core
       description: Motherboard
       product: IALAA
       vendor: TOSHIBA
       physical id: 0
       version: 1.00
       serial: 0123456789AB
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.80 (10/12/2007)
          size: 118KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer int10video acpi usb ieee1394boot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-64
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: Engineering Samplenology
          slot: Socket M2/S1G1
          size: 2200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: H0 L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-through unified
     *-memory
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: S1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: S2
             size: 1GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=fglrx_pci latency=64 module=fglrx
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0e:00.0
                logical name: eth0
                version: 01
                serial: 00:1b:38:18:d9:d4
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
        *-pci:3
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:14:00.0
                logical name: wifi0
                version: 01
                serial: 00:1b:9e:34:9e:48
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.182.186 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk
                description: ATA Disk
                product: FUJITSU MHX2250B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0040
                serial: K207T7628B56
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2869a68b
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: 19058993-edca-4997-a3e3-85dbe0366452
                   size: 2055MiB
                   capacity: 2055MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 1bbcc995-a1b8-4a60-be53-6d4df55ee18c
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-07 21:39:52 filesystem=ext3 modified=2009-07-14 17:13:57 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-07-14 17:13:57 state=mounted
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: 5786843d-fec7-48e1-84e8-b86cbbeb5fb9
                   size: 202GiB
                   capacity: 202GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-07 21:40:16 filesystem=ext3 modified=2009-07-14 17:14:01 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2009-07-14 17:14:01 state=mounted
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64 module=pata_atiixp
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RW DVR-K17LF
                vendor: PIONEER
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 4.53
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:1a:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 4.1
                bus info: pci@0000:1a:04.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:1a:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 4.3
                bus info: pci@0000:1a:04.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7 module=sdhci_pci
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-battery
       description: Lithium Ion Battery
       product: TOSHIBA
       vendor: TOSHIBA
       physical id: 1
       slot: 1st Battery
       capacity: 31500mWh
       configuration: voltage=14.8V
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: fa:b0:41:6b:04:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Thank you for all

---

### Post by zeth01 on 2009-11-11
same problem i have a razer lychesis mouse.  i've had this problem since before i installed the drivers though.  I have to re-plug the mouse in every time i restart.  not sure how to fix this. oh i should say that i have to replug every time i restart and it has to be in a different usb port.  other usb devices such as my keyboard are recognized.

---

