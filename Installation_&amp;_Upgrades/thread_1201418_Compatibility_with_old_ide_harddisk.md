---
title: "Compatibility with old ide harddisk"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by tagMacher on 2009-07-01
I had Ubuntu 6.06 running quite well on a desktop (PIII 550 MHz, 192 MB RAM, 40 GB ide Seagate harddisk), dual-booting with Win98. However since the release of 8.04 LTS, the auto update offered a distribution update which failed horribly. I tried a reinstall of 8.04 several times, but each time it was unsuccessful. The failure was always due to lots of DRDY seek error messages which I understand to be a corruption of the hard drive. IIRC The major change between 6.06 and 8.04 is the change to ext3 filesystem. I also noticed that the drives have changed from hda etc to sda etc though the harddisk and all hardware have remained the same.

My question is this: Is there an incompatibility of ext3 filesystem with old ide drives? What causes the drive corruption? I have subsequently tried a number of ther distributions including kubuntu, xubunti with xfce and Linux Mint, but have not been able to succesfully install any of these. Except for Xubuntu which failed after the first auto-update where the Linux kernel upgraded from 2.6.15 to 2.6.26.

I have verified that it is not a failing hard disk by reformating the entire disk, partitioning and checking with the Seagate Dm software that came with the hard disk and reinstalling the original win98 that had come with the system and running scadisk with /surface option (took several hours!).

I have searched using Google, but have not been able to get a clue except one place where the nomenclature change from hda to sda was explained as being due to merging of some kernel disk drive modules. This still did not explain whether ide support is discontiued in the latest linux kernels - unlikely I would think.

Request the experts on this forum to share some of their expertise and suggest a solution.

Thanks!

---

### Post by louieb on 2009-07-01
> **tagMacher said:**
> Is there an incompatibility of ext3 filesystem with old ide drives? 

Do not have a problem with older IDE drives here. 

I Have a couple of older 30GB - 40GB IDE drives one WD the other Seagate. 
They are in a P2-400mHz, 384MB memory whitebox PC. Has a minimal install of Hardy - using the Openbox window manager.

Not much help here except don't think the changes to ext3 are the reason you are having problems.

---

### Post by sanderj on 2009-07-01
What happens when you reinstall Ubuntu 6.06? Does that still work, without disk errors ... ?

---

### Post by sanderj on 2009-07-01
If you think ext3 is the problem, you can verify that by formatting as ext2.

---

### Post by tagMacher on 2009-07-04
> **sanderj said:**
> What happens when you reinstall Ubuntu 6.06? Does that still work, without disk errors ... ?


I tried with the Ubuntu 6.06.1 Desktop i386 disk. The Live CD works well, however, after the LiveCD startup the dmesg output is as follows: (only possible problem lines reproduced here). It looks like a wrong detection of a Compaq touchscreen after which there is a message about address space DMA selection for hdc CDROM drive. Susequently hdc read errors are reported.

I have checked the CD using the check disk option from the boot menu of the LiveCD and have received a all checksums okay report, so the CD seems fine but some DMA error creeps up later.

Some of the language above may seem strange but I am not a computer person. I am stuck at trying to understand the source of errors. 

Thanks for all help.


...
[17179569.184000] ACPI: Unable to locate RSDP
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0b800000:f46f0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- noacpi
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01171000)
...
[   42.823611] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x6a94, dseg 0xf0000
[   42.825563] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   42.826234] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   42.826570] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   42.826949] PnPBIOS: Missing SMALL_TAG_ENDDEP tag
[   42.827103] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[   42.827180] PCI: Probing PCI hardware
[   42.827206] PCI: Probing PCI hardware (bus 00)
[   42.827691] PCI: Ignoring BAR0-3 of IDE controller 0000:00:00.1
[   42.828341] Boot video device is 0000:01:00.0
[   42.829857] PCI: Using IRQ router SIS [1039/0008] at 0000:00:01.0
[   42.833310] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[   42.833322] PCI: Bridge: 0000:00:02.0
...
[   46.490128] SIS5513: IDE controller at PCI slot 0000:00:00.1
[   46.490197] SIS5513: chipset revision 208
[   46.490208] SIS5513: not 100% native mode: will probe irqs later
[   46.490227] SIS5513: SiS620 ATA 66 controller
[   46.490326]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:pio, hdb:pio
[   46.490380]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[   46.490429] Probing IDE interface ide0...
[   46.777845] hda: ST320423A, ATA DISK drive
[   47.449983] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   47.450525] Probing IDE interface ide1...
[   48.185463] hdc: SAMSUNG CD-R/RW SW-252S, ATAPI CD/DVD-ROM drive
[   48.857304] ide1 at 0x170-0x177,0x376 on irq 15
[   48.885781] hda: max request size: 128KiB
[   48.907465] hda: 40011300 sectors (20485 MB) w/512KiB Cache, CHS=39693/16/63, UDMA(33)
[   48.907502] hda: cache flushes not supported
[   48.908165]  hda: hda1 hda2 < hda5 hda6 >
[   48.984683] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   48.984724] Uniform CD-ROM driver Revision: 3.20
...
[  176.101339] Floppy drive(s): fd0 is 1.44M
[  176.119448] FDC 0 is a post-1991 82077
[  177.576020] ts: Compaq touchscreen protocol output
[  177.713136] PCI: Found IRQ 10 for device 0000:00:0f.0
[  181.308593] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[  181.308618] md: bitmap version 4.39
[  182.626022] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[  186.188397] cdrom: hdc: mrw address space DMA selected
...
[  223.203590] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  228.907808] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  228.907849] hdc: drive_cmd: error=0x04 { AbortedCommand }
[  228.907861] ide: failed opcode was: 0xec
...
[  592.326686] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[  592.326728] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[  592.326743] ide: failed opcode was: unknown
[  592.326759] end_request: I/O error, dev hdc, sector 1280032
[  592.326786] Buffer I/O error on device hdc, logical block 320008
[  592.978508] SQUASHFS error: sb_bread failed reading block 0x9b76a
[  592.978836] SQUASHFS error: Unable to read cache block [26dda91a:1fc2]
[  592.979091] SQUASHFS error: Unable to read directory block [26dda91a:1fc2]

---

### Post by tagMacher on 2009-07-04
> **sanderj said:**
> If you think ext3 is the problem, you can verify that by formatting as ext2.

Thanks. I will try this if I get a successful install. The installation process itself does not offer a choice of file system format.

---

### Post by sanderj on 2009-07-04
> **tagMacher said:**
> Thanks. I will try this if I get a successful install. The installation process itself does not offer a choice of file system format.

The install process *does* offer that choice: at the moment of disk partition, choose manual, and you will find format types like ext2.

---

### Post by apparle on 2009-07-04
I have an old 80GB IDE harddisk and it works just fine

---

### Post by sanderj on 2009-07-04
> **tagMacher said:**
> I tried with the Ubuntu 6.06.1 Desktop i386 disk. The Live CD works well, however, after the LiveCD startup the dmesg output is as follows: 

<snip>


So, were you able to install, boot and use 6.06.1 from your harddisk?

My guess: No. The errors you see are caused by:
- bad cd/dvd
- bad cd/dvd drive
- bad cd/dvd cable
- bad settings

As you see the problem on different CDs, it's probably not the CD, but the hardware. Easy check: use the CD in another PC. If that works, the problems is your hardware.

---

### Post by tagMacher on 2009-07-05
> **sanderj said:**
> ... 

As you see the problem on different CDs, it's probably not the CD, but the hardware. Easy check: use the CD in another PC. If that works, the problems is your hardware.


The CD checks out fine as per the checksums on the desktop as well as on another laptop , a Compaq v2414. So it must be the hardware on the desktop, which is what I have been trying to figure out. All other checks on this including installation of Win98 seems fine - its only Ubuntu that I am not able to install.

Thanks for your help - I will keep trying and report if I come across more info.

---

