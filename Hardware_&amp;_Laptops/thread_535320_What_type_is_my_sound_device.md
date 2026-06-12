---
title: "What type is my sound device?"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by donkihote on 2007-08-26
I&#8217;m just a 2 months ubuntu user, I confused to identify what my sound card is - so I can find a correct driver for it - as below attached pics that I got one on Vista and other on Festy

I appreciate any help!

---

### Post by jfinkels on 2007-08-26
> **donkihote said:**
> I’m just a 2 months ubuntu user, I confused to identify what my sound card is - so I can find a correct driver for it - as below attached pics that I got one on Vista and other on Festy

I appreciate any help!

I don't really know what your soundcard is, but you can get more info if you do ```
sudo lspci -v
``` and ```
sudo lshw 
```

---

### Post by Lord Illidan on 2007-08-26
It's probably an snd-hda-intel type of card. Have you any problems with it, like when you adjust the volume -under Ubuntu- , the sound stops?

---

### Post by donkihote on 2007-08-26
> **Lord Illidan said:**
> It's probably an snd-hda-intel type of card. Have you any problems with it, like when you adjust the volume -under Ubuntu- , the sound stops?

Thanks, It did not work at all, i tried many times with Alsa-driver to get it work but...so i need to know exactly what type it is.

---

### Post by Lord Illidan on 2007-08-27
> **donkihote said:**
> Thanks, It did not work at all, i tried many times with Alsa-driver to get it work but...so i need to know exactly what type it is.

Just type in the two commands below :

```
 sudo lspci -v 
```

and

```
 sudo lshw 
```

in the terminal, and copy their output here. Place it in CODE tags if you know how.

---

### Post by Steve1961 on 2007-08-27
You can also check what drivers are currently loaded by typing:

lsmod | grep snd

---

### Post by donkihote on 2007-08-28
Hi there,

```
ttl@ubuntu:~$ sudo lspci 
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910 
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912 
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915 
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7916 
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 7917 
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA 
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) 
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) 
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) 
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) 
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) 
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) 
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14) 
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE 
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia 
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge 
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 791f 
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01) 
14:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01) 
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 
1a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller 
ttl@ubuntu:~$  
 
 
-------------- 
 
 
  version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: pci normal_decode bus_master cap_list 
           *-display 
                description: VGA compatible controller 
                product: ATI Technologies Inc 
                vendor: ATI Technologies Inc 
                physical id: 5 
                bus info: pci@01:05.0 
                version: 00 
                size: 128MB 
                width: 64 bits 
                clock: 33MHz 
                capabilities: vga bus_master cap_list 
                configuration: driver=fglrx_pci latency=64 
                resources: iomemory:f0000000-f7ffffff iomemory:f8100000-f810ffff ioport:9000-90ff iomemory:f8000000-f80fffff irq:19 
        *-pci:1 
             description: PCI bridge 
             product: ATI Technologies Inc 
             vendor: ATI Technologies Inc 
             physical id: 5 
             bus info: pci@00:05.0 
             version: 00 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci normal_decode bus_master cap_list 
             configuration: driver=pcieport-driver 
        *-pci:2 
             description: PCI bridge 
             product: ATI Technologies Inc 
             vendor: ATI Technologies Inc 
             physical id: 6 
             bus info: pci@00:06.0 
             version: 00 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci normal_decode bus_master cap_list 
             configuration: driver=pcieport-driver 
           *-network 
                description: Ethernet interface 
                product: RTL8101E PCI Express Fast Ethernet controller 
                vendor: Realtek Semiconductor Co., Ltd. 
                physical id: 0 
                bus info: pci@0e:00.0 
                logical name: eth0 
                version: 01 
                serial: 00:1b:38:10:79:2e 
                capacity: 1GB/s 
                width: 64 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no multicast=yes port=twisted pair 
                resources: ioport:a000-a0ff iomemory:f8300000-f8300fff irq:19 
        *-pci:3 
             description: PCI bridge 
             product: ATI Technologies Inc 
             vendor: ATI Technologies Inc 
             physical id: 7 
             bus info: pci@00:07.0 
             version: 00 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci normal_decode bus_master cap_list 
             configuration: driver=pcieport-driver 
           *-network UNCLAIMED 
                description: Ethernet controller 
                product: Atheros Communications, Inc. 
                vendor: Atheros Communications, Inc. 
                physical id: 0 
                bus info: pci@14:00.0 
                version: 01 
                width: 64 bits 
                clock: 33MHz 
                capabilities: cap_list 
                configuration: latency=0 
                resources: iomemory:f8200000-f820ffff irq:20 
        *-storage 
             description: SATA controller 
             product: SB600 Non-Raid-5 SATA 
             vendor: ATI Technologies Inc 
             physical id: 12 
             bus info: pci@00:12.0 
             logical name: scsi0 
             logical name: scsi1 
             logical name: scsi2 
             logical name: scsi3 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: storage ahci_1.0 bus_master cap_list emulated scsi-host 
             configuration: driver=ahci latency=64 
             resources: ioport:8440-8447 ioport:8434-8437 ioport:8438-843f ioport:8430-8433 ioport:8400-840f iomemory:f8709000-f87093ff irq:21 
           *-disk 
                description: SCSI Disk 
                product: Hitachi HTS54161 
                vendor: ATA 
                physical id: 0.0.0 
                bus info: scsi@0:0.0.0 
                logical name: /dev/sda 
                version: SB4O 
                serial: SB2441SJCK0EPE 
                size: 149GB 
                capabilities: partitioned partitioned:dos 
                configuration: ansiversion=5 
              *-volume:0 
                   description: Primary partition 
                   physical id: 1 
                   bus info: scsi@0:0.0.0,1 
                   logical name: /dev/sda1 
                   capacity: 1500MB 
                   capabilities: primary 
              *-volume:1 
                   description: HPFS/NTFS partition 
                   physical id: 2 
                   bus info: scsi@0:0.0.0,2 
                   logical name: /dev/sda2 
                   capacity: 20GB 
                   capabilities: primary bootable 
              *-volume:2 
                   description: Extended partition 
                   physical id: 3 
                   bus info: scsi@0:0.0.0,3 
                   logical name: /dev/sda3 
                   size: 127GB 
                   capacity: 127GB 
                   capabilities: primary extended partitioned partitioned:extended 
                 *-logicalvolume:0 
                      description: HPFS/NTFS partition 
                      physical id: 5 
                      logical name: /dev/sda5 
                      capacity: 56GB 
                 *-logicalvolume:1 
                      description: HPFS/NTFS partition 
                      physical id: 6 
                      logical name: /dev/sda6 
                      capacity: 56GB 
                 *-logicalvolume:2 
                      description: Linux filesystem partition 
                      physical id: 7 
                      logical name: /dev/sda7 
                      capacity: 7224MB 
                 *-logicalvolume:3 
                      description: Linux filesystem partition 
                      physical id: 8 
                      logical name: /dev/sda8 
                      capacity: 6479MB 
                 *-logicalvolume:4 
                      description: Linux swap / Solaris partition 
                      physical id: 9 
                      logical name: /dev/sda9 
                      capacity: 1066MB 
                      capabilities: nofs 
        *-usb:0 
             description: USB Controller 
             product: SB600 USB (OHCI0) 
             vendor: ATI Technologies Inc 
             physical id: 13 
             bus info: pci@00:13.0 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ohci bus_master 
             configuration: driver=ohci_hcd latency=64 
             resources: iomemory:f8704000-f8704fff irq:17 
           *-usbhost 
                product: OHCI Host Controller 
                vendor: Linux 2.6.20-15-generic ohci_hcd 
                physical id: 1 
                bus info: usb@1 
                logical name: usb1 
                version: 2.06 
                capabilities: usb-1.10 
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s 
              *-usb 
                   description: Mouse 
                   product: Optical Wheel Mouse (USB) 
                   vendor: Mitsumi 
                   physical id: 1 
                   bus info: usb@1:1 
                   version: 1.00 
                   capabilities: usb-1.10 
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s 
        *-usb:1 
             description: USB Controller 
             product: SB600 USB (OHCI1) 
             vendor: ATI Technologies Inc 
             physical id: 13.1 
             bus info: pci@00:13.1 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ohci bus_master 
             configuration: driver=ohci_hcd latency=64 
             resources: iomemory:f8705000-f8705fff irq:18 
           *-usbhost 
                product: OHCI Host Controller 
                vendor: Linux 2.6.20-15-generic ohci_hcd 
                physical id: 1 
                bus info: usb@2 
                logical name: usb2 
                version: 2.06 
                capabilities: usb-1.10 
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s 
        *-usb:2 
             description: USB Controller 
             product: SB600 USB (OHCI2) 
             vendor: ATI Technologies Inc 
             physical id: 13.2 
             bus info: pci@00:13.2 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ohci bus_master 
             configuration: driver=ohci_hcd latency=64 
             resources: iomemory:f8706000-f8706fff irq:19 
           *-usbhost 
                product: OHCI Host Controller 
                vendor: Linux 2.6.20-15-generic ohci_hcd 
                physical id: 1 
                bus info: usb@3 
                logical name: usb3 
                version: 2.06 
                capabilities: usb-1.10 
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s 
              *-usb UNCLAIMED 
                   description: Generic USB device 
                   product: Biometric Coprocessor 
                   vendor: STMicroelectronics 
                   physical id: 2 
                   bus info: usb@3:2 
                   version: 0.01 
                   capabilities: usb-1.00 
                   configuration: maxpower=100mA speed=12.0MB/s 
        *-usb:3 
             description: USB Controller 
             product: SB600 USB (OHCI3) 
             vendor: ATI Technologies Inc 
             physical id: 13.3 
             bus info: pci@00:13.3 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ohci bus_master 
             configuration: driver=ohci_hcd latency=64 
             resources: iomemory:f8707000-f8707fff irq:18 
           *-usbhost 
                product: OHCI Host Controller 
                vendor: Linux 2.6.20-15-generic ohci_hcd 
                physical id: 1 
                bus info: usb@4 
                logical name: usb4 
                version: 2.06 
                capabilities: usb-1.10 
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s 
        *-usb:4 
             description: USB Controller 
             product: SB600 USB (OHCI4) 
             vendor: ATI Technologies Inc 
             physical id: 13.4 
             bus info: pci@00:13.4 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ohci bus_master 
             configuration: driver=ohci_hcd latency=64 
             resources: iomemory:f8708000-f8708fff irq:19 
           *-usbhost 
                product: OHCI Host Controller 
                vendor: Linux 2.6.20-15-generic ohci_hcd 
                physical id: 1 
                bus info: usb@5 
                logical name: usb5 
                version: 2.06 
                capabilities: usb-1.10 
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s 
        *-usb:5 
             description: USB Controller 
             product: SB600 USB Controller (EHCI) 
             vendor: ATI Technologies Inc 
             physical id: 13.5 
             bus info: pci@00:13.5 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ehci bus_master cap_list 
             configuration: driver=ehci_hcd latency=64 
             resources: iomemory:f8709400-f87094ff irq:20 
           *-usbhost 
                product: EHCI Host Controller 
                vendor: Linux 2.6.20-15-generic ehci_hcd 
                physical id: 1 
                bus info: usb@6 
                logical name: usb6 
                version: 2.06 
                capabilities: usb-2.00 
                configuration: driver=hub maxpower=0mA slots=10 speed=480.0MB/s 
              *-usb 
                   description: Mass storage device 
                   product: USB Mass Storage Device 
                   vendor: USBest Technology 
                   physical id: 2 
                   bus info: usb@6:2 
                   logical name: scsi4 
                   version: 1.00 
                   serial: 0000000000001A 
                   capabilities: usb-2.00 scsi emulated scsi-host 
                   configuration: driver=usb-storage maxpower=80mA speed=480.0MB/s 
                 *-disk 
                      description: SCSI Disk 
                      product: USB2FlashStorage 
                      vendor: Kingston 
                      physical id: 0.0.0 
                      bus info: scsi@4:0.0.0 
                      logical name: /dev/sdb 
                      version: 0.00 
                      size: 1999MB 
                      capabilities: removable 
                      configuration: ansiversion=2 
                    *-disc 
                         physical id: 0 
                         logical name: /dev/sdb 
                         size: 1999MB 
                         capabilities: partitioned partitioned:dos 
                       *-volume 
                            description: FAT16 partition 
                            physical id: 1 
                            logical name: /dev/sdb1 
                            capacity: 1992MB 
                            capabilities: primary bootable 
        *-serial UNCLAIMED 
             description: SMBus 
             product: SB600 SMBus 
             vendor: ATI Technologies Inc 
             physical id: 14 
             bus info: pci@00:14.0 
             version: 14 
             width: 32 bits 
             clock: 66MHz 
             capabilities: cap_list 
             configuration: latency=0 
             resources: ioport:8410-841f 
        *-ide 
             description: IDE interface 
             product: SB600 IDE 
             vendor: ATI Technologies Inc 
             physical id: 14.1 
             bus info: pci@00:14.1 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: ide bus_master 
             configuration: driver=ATIIXP_IDE latency=0 
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:8420-842f irq:17 
           *-ide 
                description: IDE Channel 0 
                physical id: 0 
                bus info: ide@0 
                logical name: ide0 
                clock: 66MHz 
              *-cdrom 
                   description: DVD-RAM writer 
                   product: HL-DT-ST DVDRAM GSA-T20N 
                   physical id: 0 
                   bus info: ide@0.0 
                   logical name: /dev/hda 
                   version: WT03 
                   serial: M2875750500 
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram 
                   configuration: mode=udma2 
                 *-disc 
                      physical id: 0 
                      logical name: /dev/hda 
        *-multimedia UNCLAIMED 
             description: Audio device 
             product: SB600 Azalia 
             vendor: ATI Technologies Inc 
             physical id: 14.2 
             bus info: pci@00:14.2 
             version: 00 
             width: 64 bits 
             clock: 33MHz 
             capabilities: bus_master cap_list 
             configuration: latency=64 
             resources: iomemory:f8700000-f8703fff irq:10 
        *-isa 
             description: ISA bridge 
             product: SB600 PCI to LPC Bridge 
             vendor: ATI Technologies Inc 
             physical id: 14.3 
             bus info: pci@00:14.3 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: isa bus_master 
             configuration: latency=0 
        *-pci:4 
             description: PCI bridge 
             product: SB600 PCI to PCI Bridge 
             vendor: ATI Technologies Inc 
             physical id: 14.4 
             bus info: pci@00:14.4 
             version: 00 
             width: 32 bits 
             clock: 66MHz 
             capabilities: pci subtractive_decode bus_master 
           *-pcmcia 
                description: CardBus bridge 
                product: PCIxx12 Cardbus Controller 
                vendor: Texas Instruments 
                physical id: 4 
                bus info: pci@1a:04.0 
                version: 00 
                width: 32 bits 
                clock: 33MHz 
                capabilities: pcmcia bus_master cap_list 
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 
                resources: iomemory:f8404000-f8404fff irq:16 
           *-firewire 
                description: FireWire (IEEE 1394) 
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
                vendor: Texas Instruments 
                physical id: 4.1 
                bus info: pci@1a:04.1 
                version: 00 
                width: 32 bits 
                clock: 33MHz 
                capabilities: ohci bus_master cap_list 
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 
                resources: iomemory:f8406000-f84067ff iomemory:f8400000-f8403fff irq:22 
           *-storage 
                description: Mass storage controller 
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 
                vendor: Texas Instruments 
                physical id: 4.2 
                bus info: pci@1a:04.2 
                version: 00 
                width: 32 bits 
                clock: 33MHz 
                capabilities: storage bus_master cap_list 
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7 
                resources: iomemory:f8405000-f8405fff irq:21 
           *-system 
                description: Generic system peripheral 
                product: PCIxx12 SDA Standard Compliant SD Host Controller 
                vendor: Texas Instruments 
                physical id: 4.3 
                bus info: pci@1a:04.3 
                version: 00 
                width: 32 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list 
                configuration: driver=sdhci latency=64 maxlatency=4 mingnt=7 
                resources: iomemory:f8406800-f84068ff irq:21 
     *-pci:1 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 101 
          bus info: pci@00:18.0 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:2 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] Address Map 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 102 
          bus info: pci@00:18.1 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:3 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] DRAM Controller 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 103 
          bus info: pci@00:18.2 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
     *-pci:4 
          description: Host bridge 
          product: K8 [Athlon64/Opteron] Miscellaneous Control 
          vendor: Advanced Micro Devices [AMD] 
          physical id: 104 
          bus info: pci@00:18.3 
          version: 00 
          width: 32 bits 
          clock: 33MHz 
  *-battery 
       description: Lithium Ion Battery 
       product: TOSHIBA 
       vendor: TOSHIBA 
       physical id: 1 
       slot: 1st Battery 
       capacity: 31500mWh 
       configuration: voltage=14.8V 
ttl@ubuntu:~$  
```

Thanks

---

### Post by Steve1961 on 2007-08-28
This is your sound card;

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia 

It seems there's a known issue with this, but also a fix at this link:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/128085](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/128085)

---

### Post by donkihote on 2007-08-29
Thanks Steve, I will follow all stuff on SB600 Azalia

---

