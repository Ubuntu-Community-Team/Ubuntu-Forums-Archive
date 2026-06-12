---
title: "Relations between ata2.00, /dev/sdb, /sys/class/scsi_host/host"
date: 2010-12-23
forum: Hardware
---

### Post by beikeland on 2010-12-23
Hi,

Sometimes I see the following errors in /var/log/kern.log
```
Dec 19 11:56:50 filebear kernel: [40952.273997] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x280100 action 0x6
Dec 19 11:56:50 filebear kernel: [40952.274004] ata2.00: BMDMA stat 0x26
Dec 19 11:56:50 filebear kernel: [40952.274010] ata2: SError: { UnrecovData 10B8B BadCRC }
Dec 19 11:56:50 filebear kernel: [40952.274016] ata2.00: failed command: READ DMA EXT
Dec 19 11:56:50 filebear kernel: [40952.274026] ata2.00: cmd 25/00:00:67:b7:d3/00:04:0b:00:00/e0 tag 0 dma 524288 in
Dec 19 11:56:50 filebear kernel: [40952.274028]          res 51/84:5f:08:b8:d3/84:03:0b:00:00/e0 Emask 0x30 (host bus error)
Dec 19 11:56:50 filebear kernel: [40952.274034] ata2.00: status: { DRDY ERR }
Dec 19 11:56:50 filebear kernel: [40952.274038] ata2.00: error: { ICRC ABRT }
Dec 19 11:56:50 filebear kernel: [40952.274048] ata2: hard resetting link
Dec 19 11:56:50 filebear kernel: [40952.748060] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 19 11:56:51 filebear kernel: [40952.784564] ata2.00: configured for UDMA/33
Dec 19 11:56:51 filebear kernel: [40952.784577] ata2: EH complete

```And while its very clear that its a failing drive, I'm having some trouble identifying the correct drive (physical location) at times.

I've normally looked at SMART status, and picked the one that has the most errors, and up until recently that worked. And then identified the drive by serial number, which is on a label in the hot-swap cage. But pulling the wrong drive from a software raid is a bad idea I've learned. 

I've looked at /dev/disk/by-* and it maps things to serials and pci busses. But I'm struggeling to find a good way to determine that ata2.00 in this case should have been /dev/sdb, and then looked up the serial for /dev/sdb.

I've also looked at  /sys/class/scsi_host/* and there seems to be a corelation beetween  scsi hostN, and ataN. By moving the drive around, I've seen the same drive attached to ata2 being refered to both /dev/sda and /dev/sdb, and in both cases also attached to host1. Is this consistent - and a good way of identifying the drive given an error for ata2.00? It looks like /dev/sdX are allocated at a first come, first served basis, but the ata and host references are static and related to physical port/controller?

and on a side note, when hotswapping support lacking, would the two approaches under be the best suited? They seem to work fine, but I'm just wanting to confirm that I have the correct understanding.

re-scan a bus
echo "0 0 0" > /sys/class/scsi_host/hostN/scan
disconecting a drive
echo "x" > /sys/class/scsi_disk/N:0:0:0/device/delete

And am I right in assuming that /sys/class/scsi_host/hostN are always present, regardless of having a drive connected, and that /sys/class/scsi_disk/N:0:0:0 are created on the fly. And the N:0:0:0 part is refering to 

[LIST]
[*]*controller ID* of the [host bus adapter]("http://en.wikipedia.org/wiki/Host_bus_adapter"),
[*]*target ID* identifying the SCSI target on that bus,
[*]*disk ID* identifying a LUN on that target,
[*]*slice ID* identifying a specific [slice]("http://en.wikipedia.org/wiki/Slice_%28disk%29") on that disk
[/LIST]
And for SATA controllers, there is a seperate controller ID for each channel? And the rest are all 0? (Thats what it looks like on my system with 82801I (ICH9 Family), SiI3132 and JMB362 controllers) at least.

---

### Post by psusi on 2010-12-23
> **beikeland said:**
> 
And am I right in assuming that /sys/class/scsi_host/hostN are always present, regardless of having a drive connected, and that /sys/class/scsi_disk/N:0:0:0 are created on the fly. And the N:0:0:0 part is refering to 

[LIST]
[*]*controller ID* of the [host bus adapter]("http://en.wikipedia.org/wiki/Host_bus_adapter"),
[*]*target ID* identifying the SCSI target on that bus,
[*]*disk ID* identifying a LUN on that target,
[*]*slice ID* identifying a specific [slice]("http://en.wikipedia.org/wiki/Slice_%28disk%29") on that disk
[/LIST]
And for SATA controllers, there is a seperate controller ID for each channel? And the rest are all 0? (Thats what it looks like on my system with 82801I (ICH9 Family), SiI3132 and JMB362 controllers) at least.

You got it.

If you look in your kernel log you should see something like this:

[    0.885633] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    0.885762] sd 0:0:0:0: [sda] Write Protect is off
[    0.885817] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.885852] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

From that you can see the scsi target that /dev/sdX is associated with.  You can also look at the directory that /sys/block/sda/device points to.

---

### Post by beikeland on 2010-12-23
I guess those lines were there all along, I just overlooked it. There  was over 1000 ata2.00 errors pr minute in the logfile, and a "few" of  hours...

$ ls -lh /var/log/kern.log
-rw-r----- 1 syslog adm 6.4G 2010-12-23 16:12 /var/log/kern.log

I thought that was a bit odd, as all previous failures have had some indication as to which block device had problems too...

Oh well, I learned a new trick (and to *check* my log files)..

---

