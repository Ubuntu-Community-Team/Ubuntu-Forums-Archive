---
title: "My built-in webcam, SD card reader and audio won´t work"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by speedisso on 2007-05-04
Hi to all
I am linux newbie and one week ago i installed Ubuntu 7.04 in my laptop, the name of the laptop is CLASUS CHALLENGER SW14 it´s made by a portugues company so they have drivers only for win
I searched all the ubuntu forums to solve my problems but i find no answer
Everthing works except built-in webcam, card reader, audio and biometria (fingerprint login windows)
Can some one help me by answering here or can contact me  [email]cmalexandru@gmail.com[/email]

---

### Post by The Foz on 2007-05-04
I have similar problems with my ACER laptop.

For mybuilt-in web-cam there is as yet no driver support. I am hoping this will be fixed in time. I suggest that you search the forum for other threads relating to web-cams. You will find guidance on how to identify exactly which web-cam hardware you have, and links for installing drivers (if one exists for your camera). Try Easycam or Easycam2 ([https://help.ubuntu.com/community/EasyCam)](https://help.ubuntu.com/community/EasyCam)).

I also have problems with my SD Card reader. It doesn't seem to get auto-mounted - I certainly haven't managed to find it anywhere. I wouldn't mind manually mounting it, if I knew the device name.

---

### Post by seshomaru samma on 2007-05-04
Can you provide more details?
What brands , what models?
If you don't know you ,I guess the laptop company's website should have some info.

---

### Post by speedisso on 2007-05-04
> **seshomaru samma said:**
> Can you provide more details?
What brands , what models?
If you don't know you ,I guess the laptop company's website should have some info.

ok , i typed in the terminal #sudo lshw and here is the list with all the hardware in the laptop


```
root@clasus-laptop:/home/speedisso# lshw
clasus-laptop             
    description: Computer
    product: A0800
    vendor: ARIMA
    version: Not Applicable
    serial: NB5733MCT04R
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=enabled uuid=436F6F70-6572-5370-7572-5F424F415244
  *-core
       description: Motherboard
       product: A0800
       vendor: ARIMA
       physical id: 0
       version: Not Applicable
       serial: Not Applicable
       slot: ADI
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: A0800F04 (07/29/2005)
          size: 92KB
          capacity: 960KB
          capabilities: isa pci pcmcia usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U1
          size: 1596MHz
          capacity: 1596MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KB
             capacity: 64KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MB
             capacity: 2MB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 512MB
          capacity: 3GB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 512MB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR Synchronous [empty]
             physical id: 1
             slot: M2
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 915GM/PM Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce Go 6200 TurboCache
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: iomemory:a0000000-a0ffffff iomemory:c0000000-cfffffff iomemory:90000000-90ffffff irq:16
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 19
                serial: 00:03:25:1c:02:60
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: iomemory:b0000000-b0003fff ioport:6000-60ff irq:16
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:4800-481f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:4820-483f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: Fingerprint Sensor
                   physical id: 2
                   bus info: usb@2:2
                   version: 6.21
                   capabilities: usb-1.10
                   configuration: maxpower=100mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:4840-485f irq:22
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:4860-487f irq:22
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Communication device
                   product: Thomson USB CDC Device
                   vendor: Thomson Inc.
                   physical id: 1
                   bus info: usb@4:1
                   version: 1.01
                   serial: 0011E31A0C59
                   capabilities: usb-1.10
                   configuration: driver=cdc_ether maxpower=100mA speed=12.0MB/s
              *-usb:1
                   description: Mouse
                   physical id: 2
                   bus info: usb@4:2
                   version: 0.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:80000000-800003ff irq:20
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 2
                bus info: pci@06:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:b4009000-b4009fff irq:18
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 2.2
                bus info: pci@06:02.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=3
                resources: iomemory:b4006000-b40067ff iomemory:b4000000-b4003fff irq:18
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 2.3
                bus info: pci@06:02.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: iomemory:b4004000-b4005fff irq:18
           *-system
                description: Generic system peripheral
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
                vendor: Texas Instruments
                physical id: 2.4
                bus info: pci@06:02.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=57 maxlatency=4 mingnt=7
                resources: iomemory:b4007000-b40070ff iomemory:b4006c00-b4006cff iomemory:b4006800-b40068ff irq:18
           *-network
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 9
                bus info: pci@06:09.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:6b:f4:34
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
                resources: iomemory:b4008000-b4008fff irq:19
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@00:1e.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:5000-50ff ioport:4880-48bf iomemory:80000800-800009ff iomemory:80000400-800004ff irq:23
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@00:1e.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
             resources: ioport:5400-54ff ioport:4c00-4c7f irq:19
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:48f0-48ff irq:19
           *-cdrom
                description: DVD writer
                product: CD/DVDW TS-L532A
                vendor: TSSTcorp
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TI51
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
           *-disk
                description: SCSI Disk
                product: SAMSUNG MP0402H
                vendor: ATA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: UC10
                serial: S03WJ10Y654114
                size: 37GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 35GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 1466MB
                   capacity: 1466MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1466MB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:4ca0-4cbf irq:10
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth2
       serial: 00:11:e3:1a:0c:59
       capabilities: ethernet physical
       configuration: broadcast=yes driver=usbnet driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=213.22.44.22 link=yes multicast=yes

```

P.S For all the moderators i am sorry for the big list but another way to solve my problems i don´t find

---

### Post by seshomaru samma on 2007-05-06
Sorry for not getting back to you,
been quite busy...
what you should do is go through the hardware list ,loacte the hardware that doesn't work and search the forum (use the search option) to find people with similar hardware and how they solved it,alternatively use [google linux]("http://www.google.com/linux")

Sorry for not being more helpfull

---

