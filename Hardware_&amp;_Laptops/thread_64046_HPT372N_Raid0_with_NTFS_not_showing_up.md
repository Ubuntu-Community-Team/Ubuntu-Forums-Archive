---
title: "HPT372N Raid0 with NTFS not showing up"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by saschxd on 2005-09-09
Hi all, 

now, after searching for nearly 3 days and trying out what i was able to, 
i can't manage to get this to work. 

i have a DFI Lanparty 875Pro mobo with an HPT372N RAID onboard controller, 
2 x 120 GB drives attached to it, NTFS formatted. 

first i thought the drives were not recognized at all, or maybe the controller (i'm really new to linux), 
so with "some" research and testing (actually 48 hrs w/o sleep and 3 ltrs of coffee) i now ended up here: 
```
CPU: Hyper-Threading is disabled
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PnPBIOS: Disabled by ACPI PNP
pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
....
ICH5: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: IBM-DTLA-307075, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 150136560 sectors (76869 MB) w/1916KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
Probing IDE interface ide1...
hdc: HL-DT-ST DVDRAM GSA-4040B, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
HPT372N: IDE controller at PCI slot 0000:02:01.0
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 17
HPT372N: chipset revision 6
hpt: HPT372N detected, using 372N timing.
FREQ: 91 PLL: 41
HPT37X: using 50MHz internal PLL
HPT372N: 100% native mode on irq 17
    ide2: BM-DMA at 0xb000-0xb007, BIOS settings: hde:DMA, hdf:pio
    ide3: BM-DMA at 0xb008-0xb00f, BIOS settings: hdg:DMA, hdh:pio
Probing IDE interface ide2...
hde: IC35L120AVV207-0, ATA DISK drive
ide2 at 0xa000-0xa007,0xa402 on irq 17
hde: max request size: 1024KiB
hde: 241254720 sectors (123522 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(33)
hde: cache flushes supported
 /dev/ide/host2/bus0/target0/lun0: p1 < >
Probing IDE interface ide3...
hdg: IC35L120AVV207-0, ATA DISK drive
ide3 at 0xa800-0xa807,0xac02 on irq 17
hdg: max request size: 1024KiB
hdg: 241254720 sectors (123522 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(33)
hdg: cache flushes supported
 /dev/ide/host2/bus1/target0/lun0: unknown partition table
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (470 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1004020k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda2, internal journal
hdc: ATAPI 32X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
Linux agpgart interface v0.100 (c) Dave Jones
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
Capability LSM initialized
...
Disabled Privacy Extensions on device c0317e40(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: disabled - APM is not SMP safe.
eth0: no IPv6 routers present
hdg: drive_cmd: status=0x58 { DriveReady SeekComplete DataRequest }

ide: failed opcode was: 0xec
hdg: status error: status=0x58 { DriveReady SeekComplete DataRequest }

ide: failed opcode was: 0xea
hdg: drive not ready for command
hdg: wcache flush failed!
hde: drive_cmd: status=0x58 { DriveReady SeekComplete DataRequest }

ide: failed opcode was: 0xec
hde: status error: status=0x58 { DriveReady SeekComplete DataRequest }

ide: failed opcode was: 0xea
hde: drive not ready for command
hde: wcache flush failed!
```
thats what i found with dmesg, 
but i have no clue on how to continue ... 
besides the problem with the RAID, you see there are other errors i don't understand, too, 
like HyperThreading disabled, kswapd0 and kseriod not stopped ( don't know what that is anyway), 
or the nvidia module tainting kernel (huh, whats that - i'm austrian) 


df -l:
Platte /dev/hde: 123.5 GByte, 123522416640 Byte
255 Köpfe, 63 Sektoren/Spuren, 15017 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/hde1               2       30034   241240072+   f  W95 Erw. (LBA)
/dev/hde5   ?       62091      208980  1179881792   3b  Unbekannt

Platte /dev/hdg: 123.5 GByte, 123522416640 Byte
255 Köpfe, 63 Sektoren/Spuren, 15017 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes

Festplatte /dev/hdg enthält keine gültige Partitionstabelle



now, first priority for me is to get the RAID problem sorted and working, 
would anyone please be so kind to assist or help me with that ? 
i posted my full dmesg output at http://pastebin.ca/22535

thanks in advance

---

