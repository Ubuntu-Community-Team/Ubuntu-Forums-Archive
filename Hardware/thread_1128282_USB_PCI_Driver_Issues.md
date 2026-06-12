---
title: "USB PCI Driver Issues"
date: 2009-04-17
forum: Hardware
---

### Post by Daniel591992 on 2009-04-17
Hi, I was trying to install a USB PCI card yesterday to get USB 2.0 on an old PC, but it did not work. Windows began to give errors so I installed Ubuntu. Unfortunately, Ubuntu does not recognize the devices either. The things I plug in are receiving power but don't do anything.

The CD that came with the drivers has two folders for Linux, but I don't know what to do with them. The first folder is called ehci1 and the second is ohci. How do I install these drivers, or is the device defective? Thanks!

---

### Post by Daniel591992 on 2009-04-17
I don't know if this helps, but:

sudo lshw -businfo
```

Bus info          Device       Class          Description
=========================================================
                               system         P6319A-ABA 750N
                               bus            P4B266LA
                               memory         64KiB BIOS
cpu@0                          processor      Intel(R) Pentium(R) 4 CPU 1.60GHz
                               memory         8KiB L1 cache
                               memory         256KiB L2 cache
                               memory         512MiB System Memory
                               memory         256MiB DIMM DRAM Synchronous
                               memory         256MiB DIMM DRAM Synchronous
pci@0000:00:00.0               bridge         82845 845 [Brookdale] Chipset Host
pci@0000:00:01.0               bridge         82845 845 [Brookdale] Chipset AGP 
pci@0000:01:00.0               display        NV34 [GeForce FX 5200]
pci@0000:00:1e.0               bridge         82801 PCI Bridge
pci@0000:02:08.0  eth0         network        82801BA/BAM/CA/CAM Ethernet Contro
pci@0000:02:09.0               bus            FW323
pci@0000:02:0a.0               bus            USB 1.1 Controller
pci@0000:02:0b.0               communication  LT WinModem
pci@0000:00:1f.0               bridge         82801BA ISA Bridge (LPC)
pci@0000:00:1f.1  scsi0        storage        82801BA IDE U100 Controller
scsi@0:0.0.0      /dev/sda     disk           80GB ST380011A
scsi@0:0.0.0,1    /dev/sda1    volume         73GiB EXT3 volume
scsi@0:0.0.0,2    /dev/sda2    volume         1466MiB Extended partition
                  /dev/sda5    volume         1466MiB Linux swap / Solaris parti
scsi@1:0.0.0      /dev/cdrom   disk           CD-R/CD-RW writer
scsi@1:0.1.0      /dev/cdrom1  disk           DVD-ROM GDR8160B
                  /dev/cdrom1  disk           
pci@0000:00:1f.2               bus            82801BA/BAM USB Controller #1
pci@0000:00:1f.3               bus            82801BA/BAM SMBus Controller
pci@0000:00:1f.4               bus            82801BA/BAM USB Controller #1
pci@0000:00:1f.5               multimedia     82801BA/BAM AC'97 Audio Controller
                  wlan0        network        Wireless interface
                  pan0         network        Ethernet interface

```

lsusb (doesn't seem to find the pci card that has an external hd plugged in)
```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 001 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

