---
title: "Built-In GPS Panasonic Toughbook CF-29"
date: 2013-03-21
forum: Hardware
---

### Post by xraynetcontrol on 2013-03-21
I've been searching and scouring the forums and Google for help, but to no avail, any help would be greatly appreciated!

I have Ubuntu 12.04 installed on a Panasonic Toughbook CF-29 with a built-in GPS device. It's dualbooted with WinXP Pro SP3. The GPS device works fine under Windoze, however, I cannot get anything to work with it in Ubuntu, and I'm not sure the system even sees it guessing from some of the error messages I see trying different things. 

Can anyone offer some suggestions? Is there anything I can copy/pasta here to help? Thank you very much in advance!

EDIT: I've included the output of lshw:

```

toughbook                 
    description: Notebook
    version: 001
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=00000000-0000-1000-8000-000B97218B0A
  *-core
       description: Motherboard
       product: CF29-2
       vendor: Matsushita Electric Industrial Co.,Ltd.
       physical id: 0
       version: 001
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies K.K.
          physical id: 0
          version: V2.00L12
          date: 04/16/2004
          size: 124KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1300MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.9.5
          slot: IC1
          size: 600MHz
          capacity: 1300MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          capacity: 2GiB
        *-bank:0
             description: TSOP DDR Synchronous
             physical id: 0
             slot: Onboard
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             physical id: 1
             slot: DIMM
             size: 1GiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 1f
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: TSOP FLASH Non-volatile
             physical id: 0
             slot: Flash ROM
             size: 512KiB
             width: 8 bits
     *-memory:2 UNCLAIMED
          physical id: 1
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e4000000-e7ffffff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: 82852/82855 GM/GME/PM/GMV Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:9 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:9 memory:e0100000-e01003ff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e02fffff memory:64000000-6bffffff
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 82
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00303020-b0030301f irq:9 memory:6c000000-6c000fff ioport:1400(size=256) ioport:3c00(size=256) memory:68000000-6bffffff memory:78000000-7bffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 82
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00704020-b0070401f irq:9 memory:70000000-70000fff ioport:3800(size=256) ioport:3400(size=256) memory:64000000-67ffffff memory:74000000-77ffffff
           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:1b:33:0c
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.103 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:9 memory:e0200000-e0200fff
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:0b:97:21:8b:0a
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.142 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:9 ioport:3000(size=256) memory:e0201000-e02010ff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:9 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:60000000-600003ff
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVE-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXCY08K04263
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=13071306
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/0C3432B134329E20
                   version: 3.1
                   serial: 60b5d7d3-5ea9-0840-9e29-9df463da7894
                   size: 157GiB
                   capacity: 157GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2012-03-23 09:22:50 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 73GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1525MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: UJDA750 DVD/CDRW
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/sr0
                version: 1.50
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:9 ioport:1c00(size=256) ioport:18c0(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
  *-battery:0
       description: Lithium Ion Battery
       product: CF-VZSU29
       vendor: Panasonic
       physical id: 1
       slot: in the front,left-hand side
       capacity: 58600mWh
       configuration: voltage=11.1V
  *-battery:1
       description: Lithium Ion Battery
       vendor: Panasonic
       physical id: 2
       slot: left-hand side

```

---

### Post by sanderj on 2013-03-21
I would start with

```
lspci
lsusb
dmesg | grep -i gps
```

and post the output here. Then google the lines that you think contain the info on your GPS device

---

### Post by xraynetcontrol on 2013-03-21
Thanks for the reply, here is the output:

**lspci**
```

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 82)
02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
spartan@TOUGHBOOK:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 154b:6545 PNY FD Device

```

**lsusb**
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 154b:6545 PNY FD Device

```

While this is now posted, Ill be using Google.

---

### Post by sanderj on 2013-03-21
I don't see anything that looks like a GPS or serial device.

Checking: "154b:6545 PNY FD Device" ... do you have a flash storage device plugged-in?

---

### Post by xraynetcontrol on 2013-03-21
Yes, the PNY FD Device is a flash storage device. After using Google on all the stuff listed there, I don't see anything that resembles a GPS receiver either. I know it's there as I use it quite often on the Windoze side of the drive, typically on port 3.

---

### Post by sanderj on 2013-03-21
> **xraynetcontrol said:**
> Yes, the PNY FD Device is a flash storage device. After using Google on all the stuff listed there, I don't see anything that resembles a GPS receiver either. I know it's there as I use it quite often on the Windoze side of the drive, typically on port 3.

"port 3"? What kind of port?

As it works in Windows, you might find the technical details / drivers / etc in Windows.

---

### Post by xraynetcontrol on 2013-03-21
In typical Windows fashion, the port number has changed (which it does sometimes). Here is all the information I got from WinXP side:

ComPort:11
HardwareID: ACPI\PNP0501
DeviceID: *pnp0501
Service: Serial
Driver Provider: Microsoft
Driver Date: 7/1/2001
Driver Version: 5.1.2600.0
Driver Files: (2) serenum.sys & serial.sys

Im not able to find much in regards to GPS with that information. Google is taking it in circles.

---

### Post by sanderj on 2013-03-21
Wondering: what is the output of:

ls -al /dev/ttyUSB*

If it gives output, maybe [http://ubuntuforums.org/showthread.php?t=1430516](http://ubuntuforums.org/showthread.php?t=1430516) is helpful

---

### Post by xraynetcontrol on 2013-03-21
All I got was "No such file or directory". Also, I have updated the first post to include the output of lshw.

---

### Post by gordintoronto on 2013-03-22
Just to make it clear: the GPS appears to be a serial device attached to what MS-DOS calls a COM port. Nothing to do with USB. It might be attached to /dev/tty3 or /dev/tty11, but I have never used serial ports in Linux.

I Googled: serial gps linux
and got lots of hits. This might be useful:
[http://catb.org/gpsd/troubleshooting.html](http://catb.org/gpsd/troubleshooting.html)

---

### Post by xraynetcontrol on 2013-03-22
> **gordintoronto said:**
> Just to make it clear: the GPS appears to be a serial device attached to what MS-DOS calls a COM port. Nothing to do with USB. It might be attached to /dev/tty3 or /dev/tty11, but I have never used serial ports in Linux.

I Googled: serial gps linux
and got lots of hits. This might be useful:
[http://catb.org/gpsd/troubleshooting.html](http://catb.org/gpsd/troubleshooting.html)

That is correct, it's a built in device, and all GPS related programs like TOPO! or Delorme Street Atlas connect to the GPS via COM port 3, or 4 whichever it feels like that day.

Thanks for the link Ill take a look and see what I can dig up there.

---

### Post by xraynetcontrol on 2013-03-23
OK, I finally have it working, tho I am not sure exactly what step I took to get it working or if it was all of them, so here is a rundown of what I did:

Searching Google for gpsd manual and tips I found that a user was getting an error like I was about permission denied when entering /dev/ttySx. I found that I needed to add myself to the "dialout" group. I did that by entering this into the terminal, and then rebooting the box:
```
sudo adduser (name) dialout
```

Once reboot was completed, I then ran the gpsd reconfiguration script in terminal:
```
sudo dpkg-reconfigure gpsd
```

The values I entered were a guess. Since my laptop has an actual serial port on the back, I guessed that the GPS receiver was in serial slot 2, so I entered ttyS2, and kept everything else as a default.

Once that was done, I entered the following from another site which stated it would start gpsd appropriately:
```
stty -F /dev/ttyS2 ispeed 4800 && cat </dev/ttys2
```

Once that was done, I tried out the GPS in terminal by using:
```
xgps
```
and
```
cgps
```

All worked. It took it about 5 minutes to get a 2D lock on me (as I was inside). One site said it could take up to 20 minutes. I closed out the terminals and launched a variety of GPS programs like GPSDrive, FoxTrot and Viking. All worked as expected.

Thank you to everyone who provided input and suggestions, I really appreciate the help!

---

