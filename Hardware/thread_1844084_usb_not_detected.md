---
title: "usb not detected?"
date: 2011-09-14
forum: Hardware
---

### Post by adasilva on 2011-09-14
Hello, One of my USB drives recently stopped working in ubuntu. It was definitely working before my fresh install of 11.04 about a month ago, but I can't be sure if I used the USB since then.

The problem: I have 2 USB slots, and one of them automounts as expected, while the other one does not work. On the nonworking slot, I plug in a USB storage device and the device appears to be busy (light on, device says it's charging, etc), but ubuntu cannot `see' it. 

Steps so far:

1. I wanted to mount it manually via the command line. However, I cannot find any entry for the usb in /dev/ (I looked for entries called sdb* and usb).

2. I tried to check fdisk, but it is not there, either:
```
~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf761d1b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9014    72404923+   7  HPFS/NTFS
/dev/sda2            9015       10838    14650369    5  Extended
/dev/sda3           10839       19326    68179860   83  Linux
/dev/sda4           19327       19457     1052257+  82  Linux swap / Solaris
/dev/sda5            9015       10586    12619776   83  Linux
/dev/sda6           10586       10838     2029568   82  Linux swap / Solaris
```

3. I checked lshw to see if the hardware is broken, assuming that if it is broken, an entry for usb will not appear on the list. (is this assumption correct?):
```

~$ sudo lshw -c bus
  *-core                  
       description: Motherboard
       product: 30CF
       vendor: Quanta
       physical id: 0
       version: 85.26
       serial: None1
     *-serial
          description: SMBus
          product: MCP67 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)
     *-usb:0
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:18 memory:f6486000-f6486fff
     *-usb:1
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:f6489000-f64890ff
     *-usb:2
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:18 memory:f6487000-f6487fff
     *-usb:3
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:f6489400-f64894ff
  *-firewire
       description: FireWire (IEEE 1394)
       product: R5C832 IEEE 1394 Controller
       vendor: Ricoh Co Ltd
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm ohci bus_master cap_list
       configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
       resources: irq:5 memory:f6100000-f61007ff

```
[EDIT: ADDITIONAL INFO]

4. 
```
~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

5. Checked the syslog:
```
Sep 14 14:16:25 ashley-laptop kernel: [13745.730114] hub 1-0:1.0: unable to enumerate USB device on port 2
Sep 14 14:16:25 ashley-laptop kernel: [13746.150114] hub 3-0:1.0: unable to enumerate USB device on port 2

```

Any advice out there?

---

### Post by adasilva on 2012-01-05
So I'm pretty sure now that my computer was broken. It may have been an issue with the motherboard because several inputs broke at around the same time including the CD-ROM and power plug, and none of them worked in windows or when booting from a live cd.

---

