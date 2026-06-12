---
title: "seagate sata woes"
date: 2008-09-22
forum: Hardware
---

### Post by Ozeuss on 2008-09-22
I have ubuntu installed on a seagate sata drive (details of lshw follows) and everything went smooth for about 3 months when my HD became all buggy on me- first the home drive had multiple errors needing a fix with fsck, and then the root partition (which required a reinstall). I am still experiencing hiccups with programs, and once the bios didn't even detect the drive.
I'm not entirely such if this is a hardware problem or a kernel/ubuntu problem. Is anyone using seagate sata?
```

  *-disk
                description: ATA Disk
                product: ST3500320AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: SD15
                serial: 9QM2SV87
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cd02b4d0
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 3e4c5df0-585c-44a8-9ad1-761041624dbb
                   size: 7726MiB
                   capacity: 7726MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-09-17 12:39:49 filesystem=ext3 modified=2008-09-19 19:04:30 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-09-19 19:04:29 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 437GiB
                   capacity: 437GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 428GiB
                      configuration: mount.fstype=ext3 mount.options=rw,nosuid,nodev,relatime,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 9546MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: 3d6be23b-ad12-4d04-b053-c45b7b5ad621
                   size: 9GiB
                   capacity: 9GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-09-19 19:05:04 filesystem=ext3 modified=2008-09-19 19:48:19 mounted=2008-09-19 19:48:19 state=clean

```

---

### Post by Kevbert on 2008-09-22
I'm using a Seagate 160Gb SATA drive along with a Western Digital 500Gb SATA drive.  The Seagate is a couple of years old, Ubuntu and XP since January with no problems regarding the drives.  
Regarding bugs have you had to do any hard resets ?  May be worth checking for damaged packages.  The other thing is that a memtest memory check may be worth doing.

---

### Post by Ozeuss on 2008-09-23
> **Kevbert said:**
> I'm using a Seagate 160Gb SATA drive along with a Western Digital 500Gb SATA drive.  The Seagate is a couple of years old, Ubuntu and XP since January with no problems regarding the drives.  
Regarding bugs have you had to do any hard resets ?  May be worth checking for damaged packages.  The other thing is that a memtest memory check may be worth doing.

Thanks for the reply. As far as i recall, it wasn't related to hard reset (i haven't done any before the problems started, but had to do it afterwards...). By "chekcing for damaged packages" do you mean fsck?
Also, i'll try the memtest...

---

### Post by Kevbert on 2008-09-23
That would be good.  To check for damaged packages you can use
```
sudo apt-get install -f
```
in terminal.

---

### Post by Ozeuss on 2008-09-23
> **Kevbert said:**
> That would be good.  To check for damaged packages you can use
```
sudo apt-get install -f
```
in terminal.

all packages are ok..

more info:
hdparm give awful transfer rates for  Timing buffered disk reads (2-4 Mb/s) but good one from cache (>1000).
dmesg-
```
 oren@ozusman:~$ dmesg | grep ata
[    0.000000]  BIOS-e820: 000000007bf90000 - 000000007bf9e000 (ACPI data)
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[   20.362967] Memory: 1989876k/2031168k available (2489k kernel code, 40904k reserved, 1318k data, 320k init)
[   20.928872] Error attaching device data
[   20.928901] Error attaching device data
[   20.928929] Error attaching device data
[   20.928961] Error attaching device data
[   23.005483] libata version 3.00 loaded.
[   23.020808] pata_amd 0000:00:08.0: version 0.3.10
[   23.021385] scsi0 : pata_amd
[   23.021665] scsi1 : pata_amd
[   23.022316] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   23.022318] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   23.187342] ata2: port disabled. ignoring.
[   24.712299] ata3: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c100 irq 508
[   24.712301] ata4: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c180 irq 508
[   24.712303] ata5: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c200 irq 508
[   24.712304] ata6: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c280 irq 508
[   25.350904] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   25.352346] ata3.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[   25.352347] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   25.354148] ata3.00: configured for UDMA/133
[   25.670713] ata4: SATA link down (SStatus 0 SControl 300)
[   26.310333] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   26.311668] ata5.00: ATAPI: Optiarc DVD RW AD-7200S, 1.04, max UDMA/100
[   26.467312] ata5.00: configured for UDMA/100
[   26.786050] ata6: SATA link down (SStatus 0 SControl 300)
[   27.172141] EXT3-fs: mounted filesystem with ordered data mode.
[   98.573736] EXT3-fs: mounted filesystem with ordered data mode.
[  362.615042] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  362.615047] ata3.00: irq_stat 0x40000001
[  362.615051] ata3.00: cmd c8/00:00:2f:c6:50/00:00:00:00:00/e0 tag 0 dma 131072 in
[  362.615053] ata3.00: status: { DRDY ERR }
[  362.615055] ata3.00: error: { UNC }
[  362.790779] ata3.00: configured for UDMA/133
[  362.790786] ata3: EH complete
[  751.552623] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  751.552627] ata3.00: irq_stat 0x40000001
[  751.552632] ata3.00: cmd 25/00:08:52:f1:c4/00:00:25:00:00/e0 tag 0 dma 4096 in
[  751.552634] ata3.00: status: { DRDY ERR }
[  751.552636] ata3.00: error: { UNC }
[  751.644225] ata3.00: configured for UDMA/133
[  751.644232] ata3: EH complete
[  754.667491] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  754.667495] ata3.00: irq_stat 0x40000001
[  754.667499] ata3.00: cmd 25/00:08:52:f1:c4/00:00:25:00:00/e0 tag 0 dma 4096 in
[  754.667502] ata3.00: status: { DRDY ERR }
[  754.667503] ata3.00: error: { UNC }
[  754.766191] ata3.00: configured for UDMA/133
[  754.766198] ata3: EH complete
[  757.872772] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  757.872777] ata3.00: irq_stat 0x40000001
[  757.872781] ata3.00: cmd 25/00:08:52:f1:c4/00:00:25:00:00/e0 tag 0 dma 4096 in
[  757.872784] ata3.00: status: { DRDY ERR }
[  757.872785] ata3.00: error: { UNC }
[  757.954723] ata3.00: configured for UDMA/133
[  757.954732] ata3: EH complete

```

---

### Post by Ozeuss on 2008-09-23
also, i don't seem to see my sata controller listed here....

```
00:0e.0 IDE interface [0101]: nVidia Corporation Unknown device [10de:07f0] (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:7366]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 508
	Region 0: I/O ports at e480 [size=8]
	Region 1: I/O ports at e400 [size=4]
	Region 2: I/O ports at e080 [size=8]
	Region 3: I/O ports at e000 [size=4]
	Region 4: I/O ports at dc00 [size=16]
	Region 5: Memory at feb7c000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [8c] #12 [0010]
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
		Address: 00000000fee0300c  Data: 4171

```

---

### Post by Kevbert on 2008-09-23
I think you should raise a bug or question in [[COLOR="Red"]launchpad[/COLOR]]("https://launchpad.net/").  The unknown and status errors are a little worrying in your dmesg log.  You can always point to this thread.
The only sata problem I've had so far is with a DVD drive which reboots the system when I try to access any DVD (CDs are fine).

---

### Post by Ozeuss on 2008-09-23
> **Kevbert said:**
> I think you should raise a bug or question in [[COLOR="Red"]launchpad[/COLOR]]("https://launchpad.net/").  The unknown and status errors are a little worrying in your dmesg log.  You can always point to this thread.
The only sata problem I've had so far is with a DVD drive which reboots the system when I try to access any DVD (CDs are fine).

Thanks Kevbert, i followed your advice- [https://bugs.launchpad.net/ubuntu/+bug/273658](https://bugs.launchpad.net/ubuntu/+bug/273658)
i hope i can find a fix.

---

### Post by Kevbert on 2008-09-23
It may take a while for the bug to be fixed.  Good luck.

---

### Post by Ozeuss on 2008-09-25
Didn't get any helpful reply from launchpad yet, but I'm in the process of scanning and repairing the HD with Seatools from seagate (i figured their own tool might be better than smartmontools).
Even if i fix that I'm still a bit worried about still ending up with a corrupt HD due to a setting I'm not aware of. Doesn't make much sense to me a 3 month old HD would fail all by itself, or does it?
Any, if you're still watching it Kevbert, or anyone else- could you please tell me your bios setting regarding the sata if it's not too much of a hassle-
I have the sata controller enabled, and the RAID mode (probably sata mode) set to IDE, and the PCI bus mastering set now to disabled (was enabled before)
and- I see from dmesg that I'm using the ahci driver and pata_amd, is that the case with you?
Thanks in Advance.

---

### Post by Kevbert on 2008-09-25
Unfortunately the Launchpad option could easily take weeks before you get a reply. If you need a quicker response you could try changing the bug into a question in Launchpad, or use one of the IRC channels (I don't know how to do this).
Regarding bios settings, my bios is Pheonix-Award.  The SATA settings are set to autodetect, SATA spread spectrum and RAID are disabled.  I couldn't find any other settings.
Regarding faulty drives, personally never had one fail, it's generally very rare, but... have you heard of the bath-tub diagram.  Initially failure early on in electronics life is very high, then failures are very low for a long period of time and eventually due to old age failures again grow. It's possible that you have a faulty drive due to batch testing (maybe 1 in 100 drives are fully tested), but unlikely.  I still think your best bet is the bug report route.

---

### Post by Ozeuss on 2008-10-03
Well, after a complete harddrive failure, i ended up sending it to for repair (i still have a warranty), and they replaced the drive. So, chicken and the egg problem here. But it might very well not be an ubuntu bug, but who knows.
Thank you for your time again, Kevbert.

---

