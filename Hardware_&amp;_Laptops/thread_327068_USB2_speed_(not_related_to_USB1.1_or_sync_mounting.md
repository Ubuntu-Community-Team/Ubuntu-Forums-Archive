---
title: "USB2 speed (not related to USB1.1 or sync mounting)"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by 16oct73 on 2006-12-28
Hi,

I've a problem with USB2 ports that I've been unable to find in previous posts.

In my case, my USB2 ports work (almost) fine, detect (and mount) whatever I attach to them, even if I unplug and plug it back several times. However, the problem is that when I copy anything to a USB storage (being a flash disk, a hard-disk, the PSP, iPod, whatever), it starts with a decent speed (10 to 20 MB/s), but after a while starts to get slower, slower, untill it stalls. 

Tests I've done:
1) If I mount the usb storage in sync mode instead of async, it uses to work, although the speed then is absolutely useless (unless for batch copy jobs). I can do this trick (i've udev rules to automatically do this with my usb hard disk) with hard drives, but I'm not going to mount sync'd any flash device (for safety reasons).
2) Doesn't look to be a "bandwidth", or bottleneck problem with the USB bus. I tried limiting the used bandwitdh (copyng with rsync --bwlimit) down to 2MB/s and it stalls anyway.
3) Some programs seem to be more tolerant than others. If I copy a couple of GB with rsync, it will stall and stop, and I'll have to umount, unplug, plug and remount. However, if the same copy is done from Konqueror, it will just decrease the speed (even to 0 B/s, and "stalled" is shown), but it usually keeps copying after some time (and several states of "stallment"). The average speed is ~300KB/s in these cases. 
4) This doesn't seem to affect other (low speed requiring) devices the USB bus. I can have a mouse working in the same hub that I have the usb storage thing, and when the usb storage is stopped, the mouse keeps going.  

I don't know who to "blame" - the USB controller (VIA, btw, I saw at google that VIA USB2 controller historically used to have problems with linux?), usb-storage, or what. Any ideas about how to troubleshoot this? Any ideas for workarounds?

thanks in advance,
k

In case it may help or you're wondering, here's lshw (and yes, it's old hw ~5 years):
-----------------cut
kikex
    description: Tower Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower
  *-core
       description: Motherboard
       product: A7V333
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS A7V333 ACPI BIOS Revision 1006 (04/17/2002)
          size: 64KB
          capacity: 192KB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp
     *-cpu
          description: CPU
          product: AMD Athlon(TM) XP 2000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.6.2
          slot: SOCKET A
          size: 1666MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KB
             capacity: 8MB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 512MB
          capacity: 3GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DDR 1
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: DDR 2
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: DDR 3
     *-pci
          description: Host bridge
          product: VT8366/A/7 [Apollo KT266/A/333]
          vendor: VIA Technologies, Inc.
          physical id: e0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: VT8366/A/7 [Apollo KT266/A/333 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 MX 440]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a3
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:d4000000-d4ffffff iomemory:d8000000-dfffffff iomemory:d7800000-d787ffff irq:177
        *-multimedia:0
             description: Multimedia audio controller
             product: CM8738
             vendor: C-Media Electronics Inc
             physical id: 5
             bus info: pci@00:05.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=C-Media PCI
             resources: ioport:d800-d8ff irq:193
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 9
             bus info: pci@00:09.0
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-386 uhci_hcd
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
             physical id: 9.1
             bus info: pci@00:09.1
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d000-d01f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.2
             bus info: pci@00:11.2
             version: 23
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:a400-a41f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-386 uhci_hcd
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
             physical id: 11.3
             bus info: pci@00:11.3
             version: 23
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:a000-a01f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-386 uhci_hcd
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
             physical id: 9.2
             bus info: pci@00:09.2
             version: 51
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:d3800000-d38000ff irq:193
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
              *-usb
                   description: USB hub
                   product: HighSpeed Hub
                   vendor: NEC Corp.
                   physical id: 1
                   bus info: usb@5:1
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
                 *-usb
                      description: Mouse
                      product: F8E842-DL Mouse
                      vendor: Belkin
                      physical id: 3
                      bus info: usb@5:1.3
                      version: 2.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-multimedia:1
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: d
             bus info: pci@00:0d.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy
             resources: ioport:b800-b81f irq:177
        *-input
             description: Input device controller
             product: SB Live! MIDI/Game Port
             vendor: Creative Labs
             physical id: d.1
             bus info: pci@00:0d.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport
             resources: ioport:b400-b407
        *-multimedia:2
             description: Multimedia video controller
             product: Bt878 Video Capture
             vendor: Brooktree Corporation
             physical id: e
             bus info: pci@00:0e.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=bttv
             resources: iomemory:d6800000-d6800fff irq:193
        *-multimedia:3
             description: Multimedia controller
             product: Bt878 Audio Capture
             vendor: Brooktree Corporation
             physical id: e.1
             bus info: pci@00:0e.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Bt87x
             resources: iomemory:d6000000-d6000fff irq:193
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: f
             bus info: pci@00:0f.0
             logical name: eth0
             version: 10
             serial: 00:c0:49:a6:f2:90
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.100.129 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:b000-b0ff iomemory:d3000000-d30000ff irq:201
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8233A ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:a800-a80f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: Maxtor 6Y160P0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: YAR41BW0
                   serial: Y42JAVWE
                   size: 152GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off smart=on
                 *-volume:0
                      description: W95 FAT32 (LBA) partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 10001MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 62MB
                      capabilities: primary
                 *-volume:2
                      description: Extended partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 16GB
                      capabilities: extended partitioned partitioned:extended
                 *-volume:3
                      description: FAT16 partition
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      capacity: 126GB
                      capabilities: primary
              *-cdrom
                   description: CD-R/CD-RW writer
                   product: HL-DT-ST GCE-8320B
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 1.04
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                 *-disc
                      physical id: 0
                      logical name: /dev/hdb
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: Hitachi HDT725032VLAT80
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: V54OA42A
                   serial: VF1200R2C67GVA
                   size: 298GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
                 *-volume:0
                      description: FAT16 partition
                      physical id: 1
                      bus info: ide@1.0,1
                      logical name: /dev/hdc1
                      capacity: 24GB
                      capabilities: primary
                 *-volume:1
                      description: FAT16 partition
                      physical id: 2
                      bus info: ide@1.0,2
                      logical name: /dev/hdc2
                      capacity: 273GB
                      capabilities: primary
              *-cdrom
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GSA-4163B
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: A104
                   serial: K0554QN2620
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
-----------------cut

---

### Post by sgreszcz on 2007-01-03
I don't have any advice, but I have the same problem here.  It is taking absolutely forever to backup my multimedia files (80GB+) to a USB2 SATA enclosure.  This is on a desktop, not a laptop however.

I'm using Ubuntu Dapper.

---

### Post by 16oct73 on 2007-01-12
more details here:
1) not to blame the specific kernel version - I tried with the kernel.org 2.6.19.1 and same thing happens.
2) not to blame the filesystem - I tried with fat32, ext3 and xfs on the USB thing and same thing happens
3) not to blame the USB controller chipset - I bought a PCI USB card with a NEC chipset instead of the VIA chipset I've in the motherboard USB's and same thing happens

Any ideas? Any troubleshooting guidance?

thx,
k

---

### Post by Sandrine_G on 2007-01-19
Hi,
Exactly same problem for me, and no idea. I've tested others distributions (Knoppix, Mepis, Debian with Kde or Gnome), no success. Motherboard Asus M2NPV-MV. 

I've found this bug reporting : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/68839](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/68839)
Sandrine

---

### Post by 16oct73 on 2007-01-29
hi,

In case this can help other users: I found the solution (at least for my particular case). 

After much testing (more than what's shown in this post) with weird results, I posted for help at linux-usb-users mail list. Following some recomendations I did some testing again, more thoroughly and found that the problem was (could be - TBH, once everything was working fine I didn't went back to check what was the particular faulty thing).

The issue was (mostly) a combination of false assumptions on my side. In some threads, I read that unpowered USB hubs tend to insert some noise and make the USB behave unpredictible. In my case, I supposed that that wasn't the case as the hub was connected to a physical connector that was not shared with the USB device I was using for testing -> WRONG! Different connectors, even when they use different inside connectors to the motherboard doesn't have to be necessarily different USB busses. This was the problem - although having 4 USB 2.0 ports, connected to 2 different motherboard connectors, they are all the same bus. 

So, I removed the unpowered bus AND used a better USB cable (those with that, um... "anti-noise cylinder" at the ends - see this picture to note what I'm referring to: [http://www.amazon.com/gp/product/images/B0000A1VS3/ref=dp_image_0/103-0989899-9207840?ie=UTF8&n=502394&s=photo](http://www.amazon.com/gp/product/images/B0000A1VS3/ref=dp_image_0/103-0989899-9207840?ie=UTF8&n=502394&s=photo) )

Since then, I've been unable to reproduce the problem.

Ah.. and about why the problem also showed up with a "fresh" USB PCI card with NEC chipset, it really doesn't showed up: it was just that the transfer speed for that card was times (5x~7x aprox.) slower than the in-board USB, and also it was not steady but "stepped", which made me though that it was stalled.

cheers,
k

---

