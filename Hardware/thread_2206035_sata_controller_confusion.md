---
title: "sata controller confusion"
date: 2014-02-17
forum: Hardware
---

### Post by astagl on 2014-02-17
I picked up a used rack server on ebay pretty cheap.  It has 12 drive bays and a SAT2-MV8 controller.  I've installed by favorite flavor of linux on it (12.04 LTS) and I'm trying to get some drives attached.

I'm running my boot disk off of a CF card which shows up in gnome-disk-utility, but I don't see anything regarding my controller.  I then assumed that it just didn't have the appropriate drivers, but when I query lspci, it looks like it is installed:

```

05:02.0 SCSI storage controller: Marvell Technology Group Ltd. MV88SX6081 8-port SATA II PCI-X Controller (rev 09)
    Subsystem: Marvell Technology Group Ltd. Device 11ab
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr+ Stepping- SERR+ FastB2B+ DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 28
    Region 0: Memory at d8200000 (64-bit, non-prefetchable) [size=1M]
    Region 2: I/O ports at 3000 [size=256]
    Region 3: [virtual] Memory at d8400000 (64-bit, non-prefetchable) [size=4M]
    [virtual] Expansion ROM at d8c00000 [disabled] [size=4M]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [60] PCI-X non-bridge device
        Command: DPERE- ERO- RBC=512 OST=4
        Status: Dev=05:02.0 64bit+ 133MHz+ SCD- USC- DC=simple DMMRBC=512 DMOST=4 DMCRS=8 RSCEM- 266MHz- 533MHz-
    Kernel driver in use: sata_mv
    Kernel modules: sata_mv

```

The server came with 4 500gb drives that I'm going to use as practice while I get used to setting up zfs. I have them installed, but I assume I should at least see the controller in disk utility, no?

[IMG]http://i.imgur.com/7w90NnG.png[/IMG]

---

### Post by TheFu on 2014-02-17
Server. Forget the GUI.
```
ls -al /dev/sd*
```

Also, **sudo parted -l** - fdisk doesn't support GPT.

---

### Post by astagl on 2014-02-17
```

(nice-rack) root [/dev] $ l sd*
brw-rw---- 1 root disk 8,  0 Feb 17 16:34 sda
brw-rw---- 1 root disk 8,  1 Feb 17 15:51 sda1
brw-rw---- 1 root disk 8,  2 Feb 17 15:51 sda2
brw-rw---- 1 root disk 8,  5 Feb 17 15:51 sda5
brw-rw---- 1 root disk 8, 16 Feb 17 16:35 sdb
brw-rw---- 1 root disk 8, 32 Feb 17 16:36 sdc

```

I guess sdb and sdc are 2 of my 4 disks showing up.  Is there a reason they don't show in the disk utility?  Also, I am running server now.  The box is headless and I have plans to keep it that way.

Thanks for your help.  Hopefully my backplane is working properly and I just have some faulty disks in there.

---

### Post by TheFu on 2014-02-17
> picked up a used rack server on ebay pretty cheap
Perhaps that explains why only a few drives are seen?
I'd pull each and connect them to another box to see if it is the drive, cable or controller that is bad.  A new LSI SAS RAID controller can be had for $400 or less.

Many disk tools will ignore drives with RAID bits as a way to protect them from accidental reuse.  May want to clear those bits before going too far ... doesn't hurt if the bits are not set either. Don't know the cmd off the top of my head. Sorry.

FYI - proper servers should have multiple backplanes and if configured by knowledgeable staff, multiple controllers inside the same box should be situated on **different** buses.

I hope all is well and just cables are bad.

---

### Post by astagl on 2014-02-17
Now I'm attempting to test out my disks and I've found that one of them is dead (maybe it's the caddy?).  I was hoping that hot swapping the drives would be a no-brainer, but it doesn't seem like that is working properly.  I tried using rescan-scsi-bus but to no avail. 

Anyone have any experience with this?

---

### Post by astagl on 2014-02-17
I really don't care so much about the drives.  I'll be filling it with my own soon, but it's good to have some to practice with.  FYI: this is the box I purchased:  [http://www.ebay.com/itm/291043618831?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1497.l2649](http://www.ebay.com/itm/291043618831?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1497.l2649)

I have so much to learn about linux hardware.  I've been using linux on AWS for a few years now, so I'm a little bit comfortable with the basics of linux.  I can get around the command line fairly well, but since all of the hardware on AWS is virtual, I never really had a need to get into the details of it.  Now that I have my own hardware, I will be absorbing all of that knowledge as well.

It's great to have the community like this; otherwise I'd be SOL.

---

