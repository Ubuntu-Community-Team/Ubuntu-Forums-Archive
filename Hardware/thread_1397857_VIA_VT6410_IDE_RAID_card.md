---
title: "VIA VT6410 IDE RAID card"
date: 2010-02-03
forum: Hardware
---

### Post by LighthouseJ on 2010-02-03
I bought one of these to put two drives into a RAID into a server of mine.  I just installed 9.10 server edition (was an older Ubuntu).  I see the device in lspci but it doesn't show up in dmesg or have /dev entries.

It looks like support was perhaps added: [in 2.6.14-rc5]("http://www.kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.14-rc5/2.6.14-rc5-mm1/broken-out/add-via-vt6410-support.patch") to the via82cxxx module.  Is that right?
I can't seem to find the module on my system, or any package in aptitude with it.  I can't find any info from ubuntu or anyone else on how to get it to show up.

If I have to reinstall w/ a different set of options, that's fine too.

Any help would be appreciated.

---

### Post by LighthouseJ on 2010-02-03
I tried to run lspci for more info and get this:

> 04:00.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
        Subsystem: VIA Technologies, Inc. VT6410 ATA133 RAID controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at dce0 [size=8]
        Region 1: I/O ports at dcd8 [size=4]
        Region 2: I/O ports at dce8 [size=8]
        Region 3: I/O ports at dcdc [size=4]
        Region 4: I/O ports at dcf0 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: pata_via


so it's loaded a kernel module?

How can I access it?

edit: here's a seemingly relevant section in the kernel messages:

> ...
[    1.560235] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20
[    1.560838] pata_via 0000:04:00.0: version 0.3.4
[    1.560850] pata_via 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.560994] scsi4 : pata_via
...

---

### Post by teejcee on 2010-04-29
Hi LighthouseJ....did you make any progress with this???

I have a PCI-IDE card with the VIA6410 chipset but I don't want to use it for RAID, just to add additional hard drives.

I'm running 9.10 64 bit with the latest kernel 2.6.31-21.  The card seems to detected ok & I can't see that there are any errors, however, the system just doesn't detect any drives attached.

---

### Post by Ocxic on 2010-04-29
With an actual RAID controller card you'll usually have to boot or run setup disk/application to get the drives setup.. with raid cards your computer will see the card itself as a drive so to speak, the card will control the drives and you computer will interact with the card. You won't get any /dev entries until you setup the proper drives and possibly partitions on the card itself,, seems as if the controller isn't programmed yet.

i found this [http://www.dowers.net/ftp/drivers/VT6421-SATApciCard/VT6421-LinuxDriverInstall.pdf](http://www.dowers.net/ftp/drivers/VT6421-SATApciCard/VT6421-LinuxDriverInstall.pdf)
hope it helps, it's not for Ubuntu but should get you started in the right direction

and try here: [http://www.via.com.tw/en/products/peripherals/](http://www.via.com.tw/en/products/peripherals/)

---

### Post by Beeker_410 on 2010-06-21
VIA raid card possible solution [https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug) This looks really confusing but I thought it might help as I'm having the same issue

---

### Post by LighthouseJ on 2010-06-21
I think I ended up getting the card to work and used "mdadm" to make a software raid-0.  I think just by setting up mdadm setup the card somehow, is my best guess.

Unfortunately the IDE drives themselves were having hardware problems (kernel was throwing disk read/write errors) so I took it all out anyway.

Sorry I can't be more help to you.

---

### Post by pigphish on 2010-06-30
what commands did you use with mdadm?

---

### Post by andrusoid on 2010-11-03
I've also had little luck with the Via VT6410 on Meerkat. In WinXP the drives show up in the diskmgmt snap-in, can be configured as raid mirror, span, or stripe set, partitioned, formatted, etc, etc.

In Meerkat, the drives simply do not appear. I've followed all the advice I've found to date here, but the drives just don't show up. dmraid -b shows all of the other drives in the system.

dmraid -s reports no raid disks, even though I created a raid1 set in windows, (formatted NTFS, ick!).

dmraid -ay -vvv -d^C finds nothing, but is clearly looking for drives in /dev. It's looking at my /dev/sda, /dev/sdb, /dev/sdc, but these are not the disks connected to the VT6410. Those disks do not have /dev entries.

Anyone have any luck with this controller in Ubuntu?

The controller shows up in the (menu) System>Administration>Disk Utility, but no drives are listed. In XP, the drives are recognized by the equivalent (but inferior) Disk Management snap-in.

Lighthouse mentioned that luck was achieved using mdadm to make a raid0 array, but wasn't sure what made it work.

---

