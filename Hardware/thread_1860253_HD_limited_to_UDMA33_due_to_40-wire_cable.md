---
title: "HD limited to UDMA/33 due to 40-wire cable"
date: 2011-10-14
forum: Hardware
---

### Post by Sirilos on 2011-10-14
Hello!

Just updated yesterday from 11.04 to 11.10. The new version of ubuntu is fantastic! :)However, all of these years have never managed to solve following problem: My Hard disk is limited to work in udma1 mode "due to 40-wire cable" which extremely slows down my system...

[PHP]sirilos@ubuntu:~$ dmesg | grep ata
[    0.000000]  BIOS-e820: 0000000027ff3000 - 0000000028000000 (ACPI data)
[    0.000000] Memory: 623452k/655296k available (5329k kernel code, 31392k reserved, 2589k data, 696k init, 0k highmem)
[    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
[    0.163288] libata version 3.00 loaded.
[    3.098974] Write protecting the kernel read-only data: 2188k
[    3.910982] pata_via 0000:00:07.1: version 0.3.4
[    4.007575] scsi0 : pata_via
[    4.016283] scsi1 : pata_via
[    4.016747] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[    4.016768] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[    4.180513] ata1.00: ATA-4: FUJITSU MPE3204AH, EH-A2-25, max UDMA/66
[    4.180539] ata1.00: 40019532 sectors, multi 16: LBA 
[    4.180572] ata1.00: limited to UDMA/33 due to 40-wire cable
[    4.196474] ata1.00: configured for UDMA/33
[    4.368625] ata2.00: ATAPI: PIONEER DVD-ROM DVD-114, 1.22, max UDMA/33
[    4.368667] ata2.01: ATAPI: Hewlett-Packard CD-Writer Plus 8100, 1.0g, max MWDMA1
[    4.376457] ata2.00: configured for UDMA/33
[    4.392430] ata2.01: configured for MWDMA1
[    5.467817] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  137.440473] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  137.440508] ata1.00: BMDMA stat 0x25
[  137.440532] ata1.00: failed command: READ DMA
[  137.440575] ata1.00: cmd c8/00:88:80:ca:a2/00:00:00:00:00/e0 tag 0 dma 69632 in
[  137.440604] ata1.00: status: { DRDY ERR }
[  137.440622] ata1.00: error: { ICRC ABRT }
[  137.440732] ata1: soft resetting link
[  137.620624] ata1.00: configured for UDMA/33
[  137.620725] ata1: EH complete
[  139.437684] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  139.437718] ata1.00: BMDMA stat 0x25
[  139.437744] ata1.00: failed command: READ DMA
[  139.437789] ata1.00: cmd c8/00:00:00:d1:ab/00:00:00:00:00/e0 tag 0 dma 131072 in
[  139.437820] ata1.00: status: { DRDY ERR }
[  139.437836] ata1.00: error: { ICRC ABRT }
[  139.437965] ata1: soft resetting link
[  139.616547] ata1.00: configured for UDMA/33
[  139.616649] ata1: EH complete
[  191.439616] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  191.439643] ata1.00: BMDMA stat 0x25
[  191.439665] ata1.00: failed command: READ DMA
[  191.439709] ata1.00: cmd c8/00:90:58:5c:aa/00:00:00:00:00/e0 tag 0 dma 73728 in
[  191.439738] ata1.00: status: { DRDY ERR }
[  191.439755] ata1.00: error: { ICRC ABRT }
[  191.439882] ata1: soft resetting link
[  191.616606] ata1.00: configured for UDMA/33
[  191.616709] ata1: EH complete
[  201.450572] ata1.00: limiting speed to UDMA/25:PIO4
[  201.450612] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  201.450635] ata1.00: BMDMA stat 0x25
[  201.450659] ata1.00: failed command: READ DMA
[  201.450703] ata1.00: cmd c8/00:00:00:d0:d3/00:00:00:00:00/e0 tag 0 dma 131072 in
[  201.450733] ata1.00: status: { DRDY ERR }
[  201.450750] ata1.00: error: { ICRC ABRT }
[  201.450878] ata1: soft resetting link
[  201.628584] ata1.00: configured for UDMA/25
[  201.628688] ata1: EH complete
[  207.433838] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  207.433872] ata1.00: BMDMA stat 0x25
[  207.433897] ata1.00: failed command: READ DMA
[  207.433941] ata1.00: cmd c8/00:00:e8:b1:08/00:00:00:00:00/e0 tag 0 dma 131072 in
[  207.433970] ata1.00: status: { DRDY ERR }
[  207.433986] ata1.00: error: { ICRC ABRT }
[  207.434110] ata1: soft resetting link
[  207.612668] ata1.00: configured for UDMA/25
[  207.612787] ata1: EH complete
[  209.439404] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  209.439436] ata1.00: BMDMA stat 0x25
[  209.439461] ata1.00: failed command: READ DMA
[  209.439504] ata1.00: cmd c8/00:50:d8:8f:08/00:00:00:00:00/e0 tag 0 dma 40960 in
[  209.439533] ata1.00: status: { DRDY ERR }
[  209.439550] ata1.00: error: { ICRC ABRT }
[  209.439667] ata1: soft resetting link
[  209.616580] ata1.00: configured for UDMA/25
[  209.616688] ata1: EH complete
[  215.439716] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  215.439753] ata1.00: BMDMA stat 0x25
[  215.439780] ata1.00: failed command: READ DMA
[  215.439826] ata1.00: cmd c8/00:00:90:4c:0d/00:00:00:00:00/e0 tag 0 dma 131072 in
[  215.439858] ata1.00: status: { DRDY ERR }
[  215.439876] ata1.00: error: { ICRC ABRT }
[  215.440166] ata1: soft resetting link
[  215.620575] ata1.00: configured for UDMA/25
[  215.620684] ata1: EH complete
[  217.444776] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  217.444810] ata1.00: BMDMA stat 0x25
[  217.444835] ata1.00: failed command: READ DMA
[  217.444878] ata1.00: cmd c8/00:00:c0:88:98/00:00:00:00:00/e1 tag 0 dma 131072 in
[  217.444909] ata1.00: status: { DRDY ERR }
[  217.444926] ata1.00: error: { ICRC ABRT }
[  217.445052] ata1: soft resetting link
[  217.624551] ata1.00: configured for UDMA/25
[  217.624653] ata1: EH complete
[  335.445662] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  335.445696] ata1.00: BMDMA stat 0x25
[  335.445721] ata1.00: failed command: READ DMA
[  335.445764] ata1.00: cmd c8/00:80:40:b8:a9/00:00:00:00:00/e1 tag 0 dma 65536 in
[  335.445793] ata1.00: status: { DRDY ERR }
[  335.445810] ata1.00: error: { ICRC ABRT }
[  335.445938] ata1: soft resetting link
[  335.624409] ata1.00: configured for UDMA/25
[  335.624492] ata1: EH complete
[  395.444816] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  395.444854] ata1.00: BMDMA stat 0x25
[  395.444879] ata1.00: failed command: READ DMA
[  395.444926] ata1.00: cmd c8/00:28:80:ec:4e/00:00:00:00:00/e2 tag 0 dma 20480 in
[  395.444959] ata1.00: status: { DRDY ERR }
[  395.444977] ata1.00: error: { ICRC ABRT }
[  395.445122] ata1: soft resetting link
[  395.624571] ata1.00: configured for UDMA/25
[  395.624662] ata1: EH complete
[  631.446518] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  631.446547] ata1.00: BMDMA stat 0x25
[  631.446570] ata1.00: failed command: READ DMA
[  631.446616] ata1.00: cmd c8/00:f8:38:39:48/00:00:00:00:00/e1 tag 0 dma 126976 in
[  631.446648] ata1.00: status: { DRDY ERR }
[  631.446664] ata1.00: error: { ICRC ABRT }
[  631.446785] ata1: soft resetting link
[  631.624393] ata1.00: configured for UDMA/25
[  631.624492] ata1: EH complete
sirilos@ubuntu:~$ 
[/PHP]

Here is also the information of hdparm:

[PHP]sirilos@ubuntu:~$ sudo hdparm -I /dev/sda
[sudo] password for sirilos: 

/dev/sda:

ATA device, with non-removable media
	Model Number:       FUJITSU MPE3204AH                       
	Serial Number:      01004251
	Firmware Revision:  EH-A2-25
Standards:
	Supported: 4 3 2 
	Likely used: 4
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:   40019532
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:       19540 MBytes
	device size with M = 1000*1000:       20490 MBytes (20 GB)
	cache/buffer size  = 2048 KBytes
Capabilities:
	LBA, IORDY(cannot be disabled)
	bytes avail on r/w long: 4
	Standby timer values: spec'd by Vendor
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: disabled
	DMA: mdma0 mdma1 mdma2 udma0 *udma1 udma2 udma3 udma4 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Power Management feature set
	    	Write cache
	   *	Look-ahead
	    	Host Protected Area feature set
	    	WRITE_BUFFER command
	    	READ_BUFFER command
	    	Advanced Power Management feature set
[/PHP]


I have been reading threads the last 3 days but not sure any more about any specific solution...

Any ideas to speed up this SCSI hard disk? Thanx in advance !

---

### Post by Sirilos on 2011-10-16
Hey.... is anyone checking this thread?

---

### Post by Sirilos on 2011-10-18
By the way, today arrived with the post a new 80 pin wire cable... I have already connected but still the problem remains the same... 

So I guess it is not a hardware problem....

---

### Post by diasf on 2011-10-18
Been a while since i hear of 40/80 pin cables....
And my money is still on hardware problem... did you check the bios for any configuration? are you sure your cable is 80? What are the errors on dmesg now?

---

### Post by slowpoke1 on 2011-12-31
I have the exact same problem.  My case may be different though.  I have a thinkpad T30 that I am using a IDE -> CF adapter.  I use a sandisk extreme 60mb/s 8 gig card.

In my other thinkpad T43, the same install, it reads as UDMA 100.  In the T30, I get the 40 pin wire problem.

I did some search and ended up using "libata.force=X:80c" in the GRUB option during boot.  This allows the change to 80 pin wire and now, in the T30, it is setup as UDMA 100 as it should.  However, hdparm -Tt /dev/sda gave fairly similar results as UDMA 33 as before.

To further test, I took out the option again so I can document the hdparm test, for whatever reason, the subsequent boot trashed the install.  I get input output errors and when I do an "ls" in home dir, I see "Bus Errors" listed.  Fsck took hours and never completes.

I try to reformat/reinstall, but the installer disk can't read/write to card neither so the card is trashed completely.

But, at least with the option set, you can get pass the 40 pin lock down.

I guess you can try it.

EDIT: Just to be clear, BIOS has been updated to latest...  not sure what other hardware I can research on the T30.

---

