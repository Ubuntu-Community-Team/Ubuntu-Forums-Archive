---
title: "Energy Management and how to have LCD backlight go off completely"
date: 2008-11-09
forum: Hardware
---

### Post by cnymike on 2008-11-09
I have read numerous posts asking about how to ensure that the LCD backlight turns off completely when the screen saver kicks in. I don't just want a "blank screensaver" which allows the backlight to continue to be on, I want the backlight to go off completely to save the tubes. 

I've never had a computer running either Windows or Mac OS, not have the ability to do this. But since I've installed XUBUNTU on my old HP Pavilion XH136 laptop, I cannot get the backlight to turn off using any of the readily available settings in the Settings Manager.

Am I just stupid, or this this a limitation of Ubuntu and Xubuntu or is it because there are no longer the original OEM drivers and such that came with the Laptop when it was running Windows... What?

I also cannot understand sleep with xubuntu. The computer goes into screen saver blank screen mode (of course with backlight still on, just black on the screen) but the comptuer does not hibernate in the sense of Windows hibernation or Mac going to sleep. IN both of those cases the computer is essentially off, in deep sleep mode, whereas with my laptop running xubuntu, it is merely in screensaver mode but it is not truly asleep no matter what the settings I choose in Screen Saver -> Power Management Preferences.

Currently those energy preferences are set to put computer to sleep in 15 minutes and put computer into Hibernate when the lid is closed. But when I close the lid, the screen goes black (backlight actually turns off in this case) but power is still on, as far as the computer is concerned since my PCMCIA slot is still powered as evidenced by the glowing LED light on my wireless card and opening the lid and hitting a key instantly results in me being wherever I was before closing the lid.

Can anyone chime in here with a solution or explanation. And yes, I'm such a beginner I can't even figure out what version of xubuntu I'm using except I know it's the latest version since it just ran updates.

---

### Post by phidia on 2008-11-09
About the version; running the updates only means it's up to date for the version you have. Opening a terminal from Applications >Accessories and entering > lsb_release -a will provide you with the version.

Getting suspend/resume/sleep functioning completely in a laptop takes some work IMO and not all hardware is supported. 
For those features it seems that all intel components are easier to get working.

If you can provide your hardware specs someone may be able to help or guide you in that better.  > lspci -v or > sudo lshw

---

### Post by cnymike on 2008-11-09
OK, here is more information as requested...



merb@hp-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

merb@hp-laptop:~$ sudo lspci -v
[sudo] password for merb: 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
	Flags: bus master, medium devsel, latency 64
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [a0] AGP version 1.0

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 128
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: f0000000-f7ffffff
	Prefetchable memory behind bridge: 30000000-300fffff

00:04.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
	Subsystem: Hewlett-Packard Company Unknown device 0014
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 30100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 24000000-27fff000
	I/O window 0: 00001c00-00001cff
	I/O window 1: 00002000-000020ff
	16-bit legacy interface ports at 0001

00:04.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
	Subsystem: Hewlett-Packard Company Unknown device 0014
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 30101000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 28000000-2bfff000 (prefetchable)
	Memory window 1: 2c000000-2ffff000
	I/O window 0: 00002400-000024ff
	I/O window 1: 00002800-000028ff
	16-bit legacy interface ports at 0001

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 1050 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at 1060 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
	Flags: medium devsel, IRQ 9

00:08.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 0012
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at 1400 [size=256]
	Capabilities: [c0] Power Management version 2

00:08.1 Communication controller: ESS Technology ESS Modem (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 0012
	Flags: medium devsel, IRQ 5
	I/O ports at 1800 [size=256]
	Capabilities: [c0] Power Management version 2

01:01.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 0014
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
	[virtual] Expansion ROM at 30000000 [disabled] [size=64K]
	Capabilities: [dc] Power Management version 1
	Capabilities: [80] AGP version 1.0

merb@hp-laptop:~$ sudo lshw
hp-laptop                 
    description: Notebook
    product: HP Pavilion Notebook PC
    vendor: Hewlett-Packard
    version: HP Pavilion Notebook XE3 GC
    serial: TW04311409
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: chassis=notebook
  *-core
       description: Motherboard
       product: N/A
       vendor: Hewlett-Packard
       physical id: 0
       version: OmniBook N32N-733
       serial: 000000000000
       slot: USB2
     *-firmware:0
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: GC.M1.63 (01/01/1992)
          size: 84KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi agp smartbattery
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.3
          slot: *Socket 7*
          size: 600MHz
          capacity: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 128KiB
             capacity: 512KiB
             capabilities: burst internal write-back
     *-firmware:1
          description: BIOS
          physical id: 50b
          size: 735KiB
          capacity: 2MiB
     *-memory
          description: System memory
          physical id: 1
          size: 255MiB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=64 module=intel_agp
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 86C270-294 Savage/IX-MV
                vendor: S3 Inc.
                physical id: 1
                bus info: pci@0000:01:01.0
                version: 11
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-1.0 vga_controller bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=4
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1420 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network
                description: Link DWL-650 11Mbps WLAN Card
                product: Version 01.02
                vendor: D
                physical id: 0
                slot: Socket 0
                resources: irq:3
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1420 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64 module=ata_piix
           *-disk
                description: ATA Disk
                product: SAMSUNG MP0603H
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: YR20
                serial: S03ZJ10L812191
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c2dcc2dc
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 627ad186-2171-45d9-8d3d-6065a14cb425
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-10-06 16:58:05 filesystem=ext3 modified=2008-11-08 22:35:28 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-11-08 22:35:28 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 721MiB
                   capacity: 721MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 721MiB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                product: CD-2800D
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 3.73
                serial: [_NEC    CD-2800D        3.730
                capabilities: removable audio
                configuration: ansiversion=5 status=open
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-multimedia
             description: Multimedia audio controller
             product: ES1988 Allegro-1
             vendor: ESS Technology
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Maestro3 latency=64 maxlatency=24 mingnt=2 module=snd_maestro3
        *-communication UNCLAIMED
             description: Communication controller
             product: ESS Modem
             vendor: ESS Technology
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
  *-battery
       physical id: 1
       slot: Right Front
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth0
       serial: 00:05:5d:d9:8d:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.3.5 ip=192.168.0.127 link=yes multicast=yes wireless=IEEE 802.11b

---

### Post by phidia on 2008-11-09
You have an S# savage video that gpu is mentioned in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/71368").
The report is older but many of the comments and potential fixes there are recent so look through them-something there will hopefully work for you.

---

