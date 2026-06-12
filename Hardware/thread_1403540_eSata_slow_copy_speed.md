---
title: "eSata slow copy speed"
date: 2010-02-10
forum: Hardware
---

### Post by bit_jammer on 2010-02-10
Hello. I've a WD 1Tb external HD connected to my Ubuntu 9.10 via eSata.
When I have to copy large amount of data (no matter if it's big files or thousands of small files) it takes ages to perform the copy (even moving files between partitions). I noticed that the behavior is always the same: it begins the copy at 25/30 MiB/s and in a couple of minutes it decreases to 2/3 MiB/s.
Do I have to change something to improve this?

Here is the information I can provide:
```
hdparam -I /dev/sdb
```
```

ATA device, with non-removable media
	Model Number:       WD My Book                              
	Serial Number:      WD-WCAU47676949
	Firmware Revision:  01.01A01
Standards:
	Used: ATA/ATAPI-6 T13 1410D revision 1 
	Supported: 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors: 1953525168
	Logical  Sector size:                   512 bytes
	Physical Sector size:                   512 bytes
	device size with M = 1024*1024:      953869 MBytes
	device size with M = 1000*1000:     1000204 MBytes (1000 GB)
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(cannot be disabled)
	Queue depth: 1
	Standby timer values: spec'd by Vendor, with device specific minimum
	R/W multiple sector transfer: Max = 1	Current = 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	   *	Power Management feature set
	   *	Write cache
	   *	48-bit Address feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART self-test
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
Integrity word not set (found 0x0000, expected 0x22a5)

```
```
hdparm -tT /dev/sdb
```
```

/dev/sdb:
 Timing cached reads:   3428 MB in  2.00 seconds = 1715.42 MB/sec
 Timing buffered disk reads:  260 MB in  3.01 seconds =  86.43 MB/sec

```

---

### Post by Varcella on 2011-03-05
I have the exact same problem and its going on my nerves.
I have read several threads with the same problem but there seems to be no help yet.

I have a Stardom HD dock running eSata and two 500 GB Hardisks in it. But it never transfer higher than 11 MB/s.

---

### Post by imwithid on 2011-06-11
I'd like to know as well. I have an HP DV4-1225dx with an eSATA+USB port and I cannot transfer files faster than about 10 MB/s. The external drive is a WD Scorpio (WD5000BPVT-00HXZT1) 500 GB 5400 RPM and the internal drive is a Seagate Momentus (ST9500420AS) 500 GB 7200 RPM. I'm almost certain that I was able to get better speeds prior to Lucid.

I do not have this problem with my desktop as I can sustain almost 38 MB/s (tested transferring 60 GB of data of varying sizes [2 MB - 4 GB). 


Using the USB alone, I can get up to about 27 MB/s sustained (not burst) on either laptop or desktop. Something is not right here.

I'm running Ubuntu 10.04.2 x64 on either computer. I will test a transfer via Windows XP x64 on the laptop to see if this is not a hardware issue unique to Ubuntu.


```
laptop:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1826 MB in  2.00 seconds = 913.29 MB/sec
 Timing buffered disk reads:  220 MB in  3.02 seconds =  72.87 MB/sec

laptop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1828 MB in  2.00 seconds = 914.45 MB/sec
 Timing buffered disk reads:  294 MB in  3.01 seconds =  97.62 MB/sec
```

---

### Post by imwithid on 2011-06-11
This seems to be an Ubuntu problem. I have a dual boot system and under Windows XP x64, I can transter a 6 GB file in under 5 minutes whereas it takes over 10 minutes under Lucid 10.04.3 x64/x86 (yes, both are affected).

---

### Post by Dyar on 2011-09-18
I've been messing with file formats on my esata disk and noticed that btfrs and Ext4 provide much greater speed than FAT or NFTS for some reason. Such as 16mb/s on NFTS and 13mb/s on FAT. Meanwhile btfrs flies at 106mb/s. It may be an odd Ubuntu error...

---

### Post by imwithid on 2011-09-20
> **Dyar said:**
> I've been messing with file formats on my esata disk and noticed that btfrs and Ext4 provide much greater speed than FAT or NFTS for some reason. Such as 16mb/s on NFTS and 13mb/s on FAT. Meanwhile btfrs flies at 106mb/s. It may be an odd Ubuntu error...

I'll try this on my laptop and see what happens. This sounds incredible. What operating system are you using currently? I'd like to test this to see if this is OS related (recall the slow USB transfer speed issue between 8.04 and 9.10) or pertaining to the file system format. Either way, this is either a bug or an AHCI driver issue (some hardware may not be fully compatible).

---

### Post by imwithid on 2011-09-20
> **Dyar said:**
> ... btfrs and Ext4 provide much greater speed than FAT or NFTS for some reason.

I can confirm this as being true in my case. Transfer rates from internal NTFS to external NTFS average approximately 11 MB/s.

Transfer rates from internal NTFS to external EXT4 average approximately 28 MB/s.

This seems to clarify the issues I've been experiencing but there is a possible inconsistency, which I have yet to test. On my desktop, I don't think transfer rates are affected by disk format type. I will test this shortly.

[EDIT]

The surprises keep coming. A rough test (not scientific by any means) presents the following results:

```
Internal NTFS to External NTFS	37 MB/s
Internal NTFS to External EXT4	34 MB/s
Internal EXT4 to External NTFS	41 MB/s
Internal EXT4 to External EXT4	35 MB/s

Internal NTFS to Internal NTFS	26 MB/s
Internal NTFS to Internal EXT4	47 MB/s
Internal EXT4 to Internal NTFS	29 MB/s
Internal EXT4 to Internal EXT4	45 MB/s

Results rounded down to the nearest whole number. Files were copied from one partition to the other. Total number of files transferred was 112 with total size being approximately 4.3 GB.

Results rounded down to the nearest whole number.
Files were copied from one partition to the other.
Total number of files transferred: 112
Total data transferred: 4.3 GB

Internal drive: Seagate 500 GB SATA-III ST3500413AS
External drive: WD 640 GB SATA-II  WDC WD6400BPVT-60HXZT1
```

File fragmentation, partition location, resource sharing, lack of reboot between transfer attempts would have led to more consistent results, however, these numbers are closer to real results on an older system (Core2 Duo circa 2006, two months after a clean install).

For two of the transfers, I had to boot from the external drive (which was faster when I repeated some of these transfers - best speed was when I booted via the external drive's Ubuntu 10.04 x86 installed OS transferring same files from the WD to the Seagate - 69 MB/s with CPU usage very high when copying from the external drive's EXT4 partition to the internal drive's EXT4 partition).

I have no comparison system to test my last comment (that an x86 version of Ubuntu may be better when transferring via eSATA than the x64 version) nor do I intend on testing it.

---

### Post by Johnius on 2012-05-04
Is this the best that eSATA can do?  I'm a little disappointed that the performance difference is negligible between eSATA and USB 2.0.  I'm getting around 30MB/s on each interface.  I was hoping I wouldn't have to sit around all day waiting for my backups.

---

