---
title: "Gyration GYR3101 is not working"
date: 2010-06-24
forum: Hardware
---

### Post by testimies on 2010-06-24
Hi

I have Gyration GYR3101 remote/air mouse. It works ok with Windows Vista, my former OS. I switched to Ubuntu 10.04 and it does not work. Remote buttons (0-9) might work once in 50 tries. Mouse movement usually doesn't work at all. Sometimes it jumps couple of centimeters and gets stuck in there.

My computer/htpc is Asus EB1501. Here is some data:

 dmesg when connecting Gyrations wireless receiver:
 
[   89.877185] usb 2-4.1: new low speed USB device using ehci_hcd and address 7
[   89.975305] usb 2-4.1: configuration #1 chosen from 1 choice
[   89.984693] input: Gyration Gyration RF Technology Receiver as /devices/pci0000:00/0000:00:06.1/usb2/2-4/2-4.1/2-4.1:1.0/input/input10
[   89.986595] gyration 0003:0C16:0002.0006: input,hiddev96,hidraw0: USB HID v1.10 Keyboard [Gyration Gyration RF Technology Receiver] on usb-0000:00:06.1-4.1/input0
[   90.002397] input: Gyration Gyration RF Technology Receiver as /devices/pci0000:00/0000:00:06.1/usb2/2-4/2-4.1/2-4.1:1.1/input/input11
[   90.006673] gyration 0003:0C16:0002.0007: input,hiddev97,hidraw1: USB HID v1.20 Mouse [Gyration Gyration RF Technology Receiver] on usb-0000:00:06.1-4.1/input1

lsusb -v:
Bus 002 Device 007: ID 0c16:0002 Gyration, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0c16 Gyration, Inc.
  idProduct          0x0002 
  bcdDevice            2.20
  iManufacturer           1 Gyration
  iProduct                2 Gyration RF Technology Receiver
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          4 USB Receiver
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     149
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.20
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     154
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

ls -la /dev/input/by-id:

lrwxrwxrwx 1 root root   9 2010-06-24 20:14 usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd -> ../event3
lrwxrwxrwx 1 root root   9 2010-06-24 20:14 usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse -> ../event4
lrwxrwxrwx 1 root root   9 2010-06-24 20:14 usb-Gyration_Gyration_RF_Technology_Receiver-mouse -> ../mouse1

Do you have any ideas? Help would be much appreciated..

Br,
TM

---

### Post by testimies on 2010-06-25
Ok. I tried to 'sudo xxd /dev/input/mouse3'. (I restarted my computer. Gyration mouse was now in mouse3) It shows mouse movement of the gyration air mouse in hex number, like this:

0000000: 38ee fb38 b5b5 38b5 c418 b52a 0846 3208  8..8..8....*.F2.
0000010: 100e 18fa 0618 ff19 38d9 b528 4bc7 18f5  ........8..(K...
0000020: 2608 1e2c 084b 2128 04b5 38e4 c309 0000  &..,.K!(..8.....

So there is definitely some movement. The problem is that I'm waving my arm like a maniac and mouse pointer just takes small jerks every now and then. It almost seems that the reception is bad in Linux. But that cannot be the case. It is still working in my old computer in the same room with Vista. Computer and OS is different. Receiver and air mouse are the same..

When I use my wireless usb mouse with the same computer those hex numbers runs happily in the screen (xxd). With Gyration one line in 3 seconds.

Same kind of bad 'reception' thing happens with remote & mouse buttons of gyration. It takes only one tenth of presses (approximately).

There must be something I'm not seeing.. :confused: Can anyone tell me where the problem could be?

Br, 
TM

---

### Post by dino99 on 2010-06-25
give the output of: lshw (need to know the real chipset name, gyration is a trademark)

---

### Post by testimies on 2010-06-25
Here it is:

```
digiboksi-yk
    description: Desktop Computer
    product: EB1501
    vendor: ASUSTeK Computer INC.
    version: 1.XX
    serial: A4ESAS000325
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=0009D1E0-27A7-4681-20C0-485B393E9EEE
  *-core
       description: Motherboard
       product: EB1501
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.XXG
       serial: 123456789000
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0904 (02/25/2010)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU 1
          size: 1600MHz
          capacity: 1666MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm pse
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 48KiB
             capacity: 48KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DDR2 Synchronous 800 MHz (1.2 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DDR2 Synchronous 800 MHz (1.2 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          size: 1600MHz
          capabilities: ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             capabilities: logical
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
             resources: ioport:2f00(size=256)
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:10 ioport:2900(size=64) ioport:2d00(size=64) ioport:2e00(size=64)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor
             description: Co-processor
             product: MCP79 Co-processor
             vendor: nVidia Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=nvidia latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:f9f80000-f9ffffff
        *-usb:0
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:17 memory:f9f7e000-f9f7efff
        *-usb:1
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:19 memory:f9f7fc00-f9f7fcff
        *-usb:2
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:16 memory:f9f7d000-f9f7dfff
        *-usb:3
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:18 memory:f9f7f800-f9f7f8ff
        *-multimedia
             description: Audio device
             product: MCP79 High Definition Audio
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
             resources: irq:20 memory:f9f78000-f9f7bfff
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
        *-storage
             description: SATA controller
             product: MCP79 AHCI Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: scsi1
             logical name: scsi2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi bus_master cap_list emulated
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:28 ioport:c080(size=8) ioport:c000(size=4) ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=16) memory:f9f76000-f9f77fff
           *-disk
                description: ATA Disk
                product: INTEL SSDSA2M040
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 2CV1
                serial: CVGB00600075040GGN
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003cdaf
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 12c969fc-668f-40c5-bc92-0951b04b1fb5
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-06-05 05:07:24 filesystem=ext4 lastmountpoint=/&#65533;&#65533;l&#1152;&#65533;&#65533;&#65533;&#526;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;>&#65533;&#65533;u^ &#65533;U/&#65533;&#65533;>&#65533;&#65533;~!&#65533; &#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;>&#65533;&#65533;&#65533;>&#65533;&#65533;a modified=2010-06-24 19:45:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-06-25 10:05:27 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 1610MiB
                   capacity: 1610MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1610MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GA10N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AT04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi bus_master cap_list
             resources: ioport:d000(size=4096) memory:fa000000-fbdfffff ioport:e0000000(size=402653184)
           *-display
                description: VGA compatible controller
                product: ION VGA
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:21 memory:fa000000-faffffff memory:e0000000-efffffff(prefetchable) memory:f6000000-f7ffffff(prefetchable) ioport:dc00(size=128) memory:fbde0000-fbdfffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:fbe00000-fbefffff ioport:f8f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 03
                serial: 48:5b:39:3e:9e:ee
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:29 ioport:e800(size=256) memory:fbeff000-fbefffff memory:f8ffc000-f8ffffff(prefetchable) memory:fbec0000-fbedffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:fbf00000-fbffffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 01
                serial: 1c:4b:d6:ba:b7:0b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.0.103 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 memory:fbff0000-fbffffff
        *-pci:4
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26
        *-pci:5
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 18
             bus info: pci@0000:00:18.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27
     *-scsi
          physical id: 2
          bus info: usb@1:2
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sdb

```

---

### Post by dino99 on 2010-06-25
hm, that does not help

found several links:

[http://www.mythtv.org/wiki?title=Gyration-based_MCE_Remotes&redirect=no](http://www.mythtv.org/wiki?title=Gyration-based_MCE_Remotes&redirect=no)
( [COLOR="Blue"][SIZE="3"]scroll down to Linux installation[/SIZE][/COLOR])

other links in case:

[http://perens.com/works/software/gyration.html](http://perens.com/works/software/gyration.html)
(outdated for the first part as some packages does not exist into the latest ubuntu distro, but the second part is ok)

[http://wiki.linuxmce.org/index.php?title=GYR3101_Integration_Notes&redirect=no](http://wiki.linuxmce.org/index.php?title=GYR3101_Integration_Notes&redirect=no)

[http://guide.ubuntuforums.org/showthread.php?t=1048603](http://guide.ubuntuforums.org/showthread.php?t=1048603)

---

### Post by testimies on 2010-06-25
Thanks! I'll check those out.

---

### Post by testimies on 2010-06-27
..... :confused: This is weird. Day before yesterday I started to go though those pages. I had seen them before and I felt like those pages were about different kind of problem. They were fixing problem where one or two buttons were missing. My problem was that remote's mouse functionality was not working.

I started computer today and without changing anything it is working!?????!! Mouse is moving nicely (there is minor jerking still left but almost unnoticeable) , button are working... I am starting to suspect that I have problems with my usb ports. On hw or on sw(kernel??) level. There is another thing that indicates to that direction. Sometimes Ubuntu won't start when I have my usb hub attached to it. It goes to that screen with Ubuntu text and couple of red dots underneath it. It just gets stuck there and I have to reboot it. (5 seconds power button) After I detach usb hub and put it back when Ubuntu is in login screen everything is fine.

Usb thing is bigger problem and I hope I don't have to try to fix it. Otherwise I'm screwed! (If I won't turn it off?? Linux should run for years without reboot???)

Thanks Dino99 for help.

---

### Post by testimies on 2010-07-07
It seems that I have problems with hardware. Maybe Gyration's RF receiver isn't standard usb device, maybe my computer is broken. Gyration's air mouse movement "quality" changes every time I restart my computer. Sometimes it's normal, like mouse should be, most of the times it isn't, jumping small steps around. It varies from smooth movement to no movement at all.

I have tried it with Ubuntu Live CD and Puppy Linux live CD just to eliminate possibility that some programs I have installed might interfere with it. I have latest BIOS version... 

I should have tried it with windows that was pre-installed in EB1501. I was too eager to switch to Linux..

Nevermind, I bought new one :p. Cideko air keyboard. I hope it doesn't have same problems.

[http://www.gadgetreview.com/2009/06/cideko-air-keyboard-incorporates-an-air-mouse-keyboard-and-media-controls.html](http://www.gadgetreview.com/2009/06/cideko-air-keyboard-incorporates-an-air-mouse-keyboard-and-media-controls.html)

---

