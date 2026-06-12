---
title: "csatacombo from conceptronic under gutsy"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by anatol_w on 2008-04-07
howdy folks,
i just got into this forum, even being an ubuntu / debian / etc. user for some years now.
recycling hardware got its problems, mine is that the IDE controller on the main board does only control one at the time (2 devices only).
so i got the csatacombo from conceptronic just to plug the dvd recorder / reader.
i know the things coming from conceptronic do quite some strange things under any linux distro, but this was the only card inside the budget.
recently i switched from dapper to gutsy since it made no sense to me having gutsy on my laptop and dapper on the desktop (needing nfs tweaks etc).
since that switch the devices plugged to the card simply misbehave:
i'm not able to burn CD's or DVD's (gnome does not detect anything in the drive at all and just gives me the blank CD icon, recording though is only possible to an file image)
k3b does detect the recorder correctly but does not burn anything (just sits there spinning the drive)


lspci:
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
02:09.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
02:0b.0 SCSI storage controller: Adaptec AIC-7861 (rev 01)
02:0c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
02:0d.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:0d.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
02:0d.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
02:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

as you can see the card shows up as a via chipset VT6421

the interesting part of lshw:
 *-storage
                description: RAID bus controller
                product: VT6421 IDE RAID Controller
                vendor: VIA Technologies, Inc.
                physical id: 9
                bus info: pci@0000:02:09.0
                logical name: scsi2
                version: 50
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list emulated
                configuration: driver=sata_via latency=32 module=sata_via
              *-cdrom:0
                   description: SCSI CD-ROM
                   physical id: 0.0.0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/cdrom2
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   capabilities: audio
                   configuration: status=open
              *-cdrom:1
                   description: SCSI CD-ROM
                   product: CD-S400/A
                   vendor: ASUS
                   physical id: 0.1.0
                   bus info: scsi@2:0.1.0
                   logical name: /dev/cdrom
                   logical name: /dev/scd1
                   logical name: /dev/sr1
                   version: 1.1C
                   capabilities: removable audio
                   configuration: ansiversion=5 status=open

the secondary cdrom is detected "correctly" but is incredibly slow, he master, however should be a dvdram.

any hints anyone?!
is there a way to backport the drivers from dapper?

thanks

[www.anatol.biz](www.anatol.biz)

---

