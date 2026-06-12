---
title: "Ubuntu running extremely SLOW!"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by unewbuntu on 2007-02-26
Hey,

I am new to ubuntu, however I would not consider my self a computer illiterate in anyway.

This is my problem,

I installed Ubuntu on my extra desktop the other day, the desktop has the following specs,

Os: Ubuntu 6.06 Dapper 32 Bit Edition
Motherboard: VIA PM8M-V Series (MS-7104 v2.X) M-ATX mainboard
CPU: Intel(R) Pentium(R) 4 CPU 1.70GHz
Chipset VIA P4M800 chipset (645 BGA)
Main memory: 1GB
Swap memory: 1.5 GB (AUTO)
Harddrive space: 38.5 GB
Microsoft Standard wireless Keyboard & Mouse (Talk about irony!!!)
D-link G132 wireless card

On initial install the only obvious problem I could see was that my wireless card refused to work, HOWEVER after installing Ndiswrapper I managed to get it to work.

MY PROBLEM:

The main problem I have noticed is that my system is RIDICULOUSLY!! slow

Sure, I don't expect lightning fast speeds on a 1.7GHZ however to put it into perspective, my laptop running 1.6GHZ processor with 512 mb ram running Windows XP Pro runs about 5 times as fast.

It feels almost slower then the live cd it self (no exaguration) with it being hard to open anything more then 1 tab at a time with firefox.

I tried figuring out whats wrong but i'm baffled (being new to ubuntu)


Here is a dump from, lshw

user@Artic:~$ sudo lshw
Password:
```

artic
    description: Desktop Computer
    product: MS-7104
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    version: 20A
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MS-7104
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 20A
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/22/2006)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1.70GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.1.3
          slot: Socket 478
          size: 1700MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 8KB
             capacity: 20KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-cpu:1 DISABLED
          description: CPU
          product: ( )
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: 15.1.3
          slot: Socket 478
          size: 1700MHz
          clock: 100MHz
          capabilities: ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 8KB
             capacity: 20KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 1GB
          capacity: 1GB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MB
     *-pci:0
          description: Host bridge
          product: P4M800CE Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: e8000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:e8000000-efffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f4000000-f7ffffff iomemory:fb000000-fbffffff irq:10
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@00:0f.0
             logical name: scsi0
             logical name: scsi1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=sata_via
             resources: ioport:fc00-fc07 ioport:f800-f803 ioport:f400-f407 ioport:f000-f003 ioport:ec00-ec0f ioport:e800-e8ff irq:169
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:e400-e40f irq:169
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: SAMSUNG SV4012H
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: RM100-10
                   serial: 0540J1BW250818
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 35GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 1576MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: TSSTcorpCD/DVDW SH-S162A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: TS01
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:e000-e01f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:dc00-dc1f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Keyboard
                   product: Microsoft Wireless Optical Desktop
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.41
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:fdfff000-fdfff0ff irq:177
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-26-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: Generic USB device
                   product: USB WLAN Device
                   vendor: Atheros Communications Inc
                   physical id: 4
                   bus info: usb@5:4
                   version: 0.01
                   serial: 1.0
                   capabilities: usb-2.00
                   configuration: driver=ndiswrapper maxpower=0mA speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:d000-d0ff irq:193
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 78
             serial: 00:**:**:d3:**:ca
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
             resources: ioport:cc00-ccff iomemory:fdffe000-fdffe0ff irq:185
     *-pci:1
          description: Host bridge
          product: P4M800CE Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: P4M800CE Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: P4M800CE Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: P4M800CE Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1*:**:*9:4*:**
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.102 link=yes multicast=yes wireless=IEEE 802.11g

```

user@Artic:~$ sudo lshw -C disk
```

  *-disk
       description: ATA Disk
       product: SAMSUNG SV4012H
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: RM100-10
       serial: 0540J1BW250818
       size: 37GB
       capacity: 37GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma5 smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.0,1
          logical name: /dev/hda1
          capacity: 35GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: ide@0.0,2
          logical name: /dev/hda2
          capacity: 1576MB
          capabilities: extended partitioned partitioned:extended
  *-cdrom
       description: DVD-RAM writer
       product: TSSTcorpCD/DVDW SH-S162A
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: TS01
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdc

```


Anything else you'll need from me, go ahead and ask.

I appreciate anyone putting into time to help me out.

---

### Post by Biggus on 2007-02-26
I can't help you in fashion other than to confirm what you already know, there is a problem with your installation.

I'm a relative ubuntu noob, and I can say I didn't notice any difference (maybe a slightly quicker startup time in Firefox) when I changed over from XP with regards to browsing.

For browsing, looking at your specs, your system should be flying along.

---

### Post by twk3 on 2007-02-26
Umm, I'm new to ubuntu as well, but I noticed, that your South Bridge Chipset is Unclaimed (no driver loaded).... that should cause some SERIOUS problems. Without the South Bridge your pci's shouldn't even be working. So that can't be right. I would suggest figuring out how to get that fixed though.

---

### Post by drdnl on 2007-03-29
I just fixed this problem on my gf's pc (well, i think you have the same problem)

There's no SWAP, the partition is there, but its not mounted in ubuntu.

first, check the presence of the 1.5gb swap auto you mentioned:

sudo fdisk -l

it should be under say, hda5 

Now check your mounts with 

nano /etc/fstab 

It might say /dev/hda5 (for example) but it might also be under a weird cryptic UUID.

My advice would be to edit the fstab

gksu gedit /etc/fstab

remove the line that (is attempting to) reference your swap completely, it might be quite long due to the aforementioned UUID

and insert this
/dev/hda5	none 		swap 	sw 		0 	0

once, again, just to be sure (i'm not implying you're stupid :)), change hda5 to whatever is your swap drive.

Reboot

Check your swap with either "top" in terminal or using the system monitor.

Hope this helps
ps. its been 4 weeks, either you fixed it or you've given up. If its the latter, keep trying, i've been using linux now for 9 months and loving it.

---

### Post by unewbuntu on 2007-03-29
hmm wow..

this certainly is lucky lol, I gave up on ubuntu about the day after I made the post and luckily enough last night I decided to give Kubuntu 7.0.4 a try (since i just realized I like KDE better)

anyway I checked out the readings from top and its showing swap memory being used is 0k so I am guessing this was the problem, I am just about to make the changes and see what happens.

Ill come back and post if it works.

Thanks a lot!

---

### Post by drdnl on 2007-03-29
No problem, I know it was driving my girlfriend crazy (so.... amazingly..... SLOW.....). One thing though, just because it says 0k doesn't necessarily mean there's something wrong.

For a more thorough check try running "top" (simply top) in the terminal and check whether it looks something like this:

Mem:    516056k total,   440632k used,    75424k free,    11972k buffers
Swap:   554200k total,    10652k used,   543548k free,   224752k cached

if yours says swap 0k 0k 0k then yes, there's something wrong.

Regards,
D

(wonder how common a bug this is?)

and ps. I didnt stick with linux the first time I tried it (5.10) somewhere in February, so confusing... But when 6.06 came out shortly after, and the "Polish" had improved tremendously I stuck it out. Even deleted Windows for 3 months, barely missed it :)
Just stick around, you'll get the hang of it.

---

### Post by unewbuntu on 2007-03-29
npe actually no luck.. still shows 0k... hmm any other ideas..?

---

### Post by drdnl on 2007-03-29
What says 0k, does top say 0k available?

---

### Post by drdnl on 2007-03-30
Left you a pm

---

