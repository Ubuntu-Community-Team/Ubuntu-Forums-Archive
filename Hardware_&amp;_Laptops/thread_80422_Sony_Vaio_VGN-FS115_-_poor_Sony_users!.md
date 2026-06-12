---
title: "Sony Vaio VGN-FS115 - poor Sony users!"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by igor4u on 2005-10-22
Very bad work Breezy! :mad: 

* No sound
* USplash stop
* No true colors on display - only 256
* Freeze after reboot
* Not working Fn

Could somebody help me? :confused:

---

### Post by edal on 2005-10-22
Sony PCG-K415B

Sound works first time
No freezing
All colors available on display at the correct resolution
Function keys are not working but an alternative found after thirty minutes

In fact the ONLY problems I have with Breezy running on this laptop are the battery life and the battery charge indicator. Try running Fedora on your machine then you will really see a list of problems.

Ed Almos

---

### Post by thom_kbbc on 2005-10-22
[QUOTE=igor4u]Very bad work Breezy! :mad: 

* No sound
* USplash stop
* No true colors on display - only 256
* Freeze after reboot
* Not working Fn

Could somebody help me? :confused:[/QUOTE]
I've no problems on my FS115B, have a look at my page : [http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)

---

### Post by blackpaw on 2005-10-23
PCG-N505SN and PCG-Z600TEK

both running Breezy out of the box, no issues. Even Fn-Keys working fine.
Well, I guess there are a lot of VAIOs out there, but please don't make them (the Ubuntu-people/SONY VAIOs) bad only because _yours_ isn't working.

ciao,


andreas

---

### Post by igor4u on 2005-10-23
[QUOTE=thom_kbbc]I've no problems on my FS115B, have a look at my page : [http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)[/QUOTE]

Thank you. I know it's strange why my laptop doesn't work correct with Breezy.
Maybe your tutorial will help me. I hope. :p

---

### Post by basscad on 2005-10-23
[QUOTE=thom_kbbc]I've no problems on my FS115B, have a look at my page : [http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)[/QUOTE]

Hi all

im a poor sony pcg-k415b user

i installed ubuntu 5.10 this afternoon and everything (except built in modem) worked excellent utnil first reboot. my sony crashes when its about to show the login window. when system starts i get "temporary name resolution error". so i looked at above site, dled 915resolution-0.4.7 and followed ur steps until the middle of step 2 :)  when i type "make" and "sudo make install" i get "no such command error".
i had the smae problem when i tried mandrake 10.1 (works fine until first reboot)

im a complete noob, but id like to improve :)
im begging for help



help

---

### Post by thom_kbbc on 2005-10-24
you have to install the "make" package : 
```
sudo apt-get install make
```

---

### Post by basscad on 2005-10-24
thanx tom

unfortunately my pcg-k415b runs on ati chipset which is not supported by the 915resolution hack... :/

but at least now i know wheres the problem :)

---

### Post by thom_kbbc on 2005-10-24
What does ```
lshw | grep "Graphics Controller"
``` gives ?

---

### Post by basscad on 2005-10-24
hmmm

well like i said at the beginning im a complete noob :)

the answer is "i dont know". when i type the code i can see sth flashing very quickly in one line (i can distinguish words like PCI sth, USB?, buffer, sth device) until it disapears "behind" a prompt...

---

### Post by no1wantdthisname on 2005-10-25
Vaio VGN FS640/W here.

The FS series has a problem with fn keys.  Got mine to work going here.
[http://forums.gentoo.org/viewtopic-p-2722251.html#2722251](http://forums.gentoo.org/viewtopic-p-2722251.html#2722251)

Mute, volume up/down and brightness up/down work.  

Hibernate tries to execute some script, but since this was originally for Gentoo it doesn't work.  I don't use hibernate anyway so haven't tested.

---

### Post by thom_kbbc on 2005-10-25
If you lunch a prompt, and then the command ? 
juste type ```
$ lshw
``` and report the output here

---

### Post by basscad on 2005-10-25
[QUOTE=thom_kbbc]If you lunch a prompt, and then the command ? 
juste type ```
$ lshw
``` and report the output here[/QUOTE]

here i am:

vaio
    description: Notebook
    product: PCG-K415B
    vendor: Sony Corporation
    version: C100M9Y5
    serial: 28194060-5202076
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=BA8946C0-F356-11D7-8CCA-00014A09E922
  *-core
       description: Motherboard
       product: Q-Project
       vendor: Sony Corporation
       physical id: 0
       version: 02
       serial: 12345678-12345678
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0106X3 (10/26/2004)
          size: 115KB
          capacity: 448KB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: N/A
          size: 3060MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 8KB
             capacity: 8KB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 256KB
             capacity: 256KB
             capabilities: asynchronous external write-back data
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3 Cache
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: SODIMM DDR 133 MHz (7.5 ns)
             product: N/A
             vendor: N/A
             physical id: 0
             serial: N/A
             slot: SODIMM1
             size: 256MB
             width: 32 bits
             clock: 133MHz (7.5188ns)
        *-bank:1
             description: SODIMM DDR 133 MHz (7.5 ns)
             product: N/A
             vendor: N/A
             physical id: 1
             serial: N/A
             slot: SODIMM2
             size: 256MB
             width: 32 bits
             clock: 133MHz (7.5188ns)
     *-pci
          description: Host bridge
          product: RS200/RS200M AGP Bridge [IGP 340M]
          vendor: ATI Technologies Inc
          physical id: e8000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 66MHz
          resources: iomemory:e8000000-efffffff iomemory:e0600000-e0600fff
        *-pci
             description: PCI bridge
             product: PCI Bridge [IGP 340M]
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon IGP 330M/340M/350M
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@01:05.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f0000000-f7ffffff ioport:a000-a0ff iomemory:e0300000-e030ffff irq:4
        *-communication
             description: Modem
             product: M5457 AC'97 Modem Controller
             vendor: ALi Corporation
             physical id: 3
             bus info: pci@00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: driver=serial
             resources: iomemory:2c000000-2c000fff ioport:1000-10ff irq:10
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 4
             bus info: pci@00:04.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=ALI 5451
             resources: ioport:8400-84ff iomemory:e0005000-e0005fff irq:10
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus
        *-isa UNCLAIMED
             description: ISA bridge
             product: M1533 PCI to ISA Bridge [Aladdin IV]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-network:0 DISABLED
             description: Wireless interface
             product: AR5212 802.11abg NIC
             vendor: Atheros Communications, Inc.
             physical id: 9
             bus info: pci@00:09.0
             logical name: ath0
             version: 01
             serial: 00:0e:9b:8e:94:c5
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11
             resources: iomemory:2c010000-2c01ffff irq:11
        *-pcmcia
             description: CardBus bridge
             product: PCI7420 CardBus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:e0006000-e0006fff irq:4
        *-firewire
             description: FireWire (IEEE 1394)
             product: PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
             vendor: Texas Instruments
             physical id: a.2
             bus info: pci@00:0a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci cap_list
             configuration: driver=ohci1394
             resources: iomemory:e000b000-e000b7ff iomemory:e0000000-e0003fff irq:10
        *-storage UNCLAIMED
             description: Unknown mass storage controller
             product: PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. and SD/MS-Pro Sockets
             vendor: Texas Instruments
             physical id: a.3
             bus info: pci@00:0a.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: storage cap_list
             resources: iomemory:e0007000-e0007fff irq:255
        *-usb:0
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: c
             bus info: pci@00:0c.0
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:e0009000-e0009fff irq:10
           *-usbhost
                product: NEC Corporation USB
                vendor: Linux 2.6.12-9-386 ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@1:1
                   version: 29.01
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=50mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: c.1
             bus info: pci@00:0c.1
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:e000a000-e000afff irq:6
           *-usbhost
                product: NEC Corporation USB (#2)
                vendor: Linux 2.6.12-9-386 ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: NEC Corporation
             physical id: c.2
             bus info: pci@00:0c.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e000b800-e000b8ff irq:11
           *-usbhost
                product: NEC Corporation USB 2.0
                vendor: Linux 2.6.12-9-386 ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=5 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: USB Flash Memory
                   vendor: Toshiba Corp.
                   physical id: 2
                   bus info: usb@3:2
                   logical name: scsi2
                   version: 1.00
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: USB Flash Memory
                      physical id: 0.0.0
                      bus info: scsi@2.0:0.0
                      logical name: /dev/sda
                      version: 1.00
                      size: 489MB
                      capabilities: removable
                      configuration: ansiversion=2
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: f
             bus info: pci@00:0f.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ALI15x3_IDE
             resources: ioport:8080-808f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: HTS424040M9AT00
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: MA2OA71A
                   serial: MPA242Q2CZMVTB
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm
                   configuration: apm=off mode=udma5 smart=on
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD writer
                   product: SONY DVD RW DW-D56A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: PFS3
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2
        *-network:1 DISABLED
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 10
             serial: 00:01:4a:09:e9:22
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
             resources: ioport:9000-90ff iomemory:e000bc00-e000bdff irq:3


just in case printed everything, maybe ull spot some other bugs :) (i found a couple btw)

i hope i didnt display anything confidential, i wouldnt want anyone to hurt my little freind... :)

i can see it displays my chipset as igp 340m, but specification says its 345m

what i dont understand is why does it WORK right after installation, until the first reboot?? if sths wrong with hardware compatibility it shouldnt start in the first place, should it? i can also hibernate/wake without any issues...

---

### Post by basscad on 2005-10-29
:)

im viewing this site in mozilla firefox... now how cool is that...

i tried ubuntu 4.10. it did work but everytime i restarted some xfree error was coming up, so i installed 5.04 and... it works...

i managed to install my modem, now a new task - mounting wondows partitions..
wish me luck

thx

---

### Post by igor4u on 2005-10-29
[QUOTE=igor4u]Very bad work Breezy! :mad: 

* No sound
* USplash stop
* No true colors on display - only 256
* Freeze after reboot
* Not working Fn

Could somebody help me? :confused:[/QUOTE]

NOW WORKS: :smile: 
* Sound works already fine (I found sound was off after fresh install)
* Good screen colors (added Nvidia driver)

NOT WORK: :( 
* USplash :( 
* Freeze after reboot, sometimes after hibernation :mad: :( 
* Not working Fn

---

