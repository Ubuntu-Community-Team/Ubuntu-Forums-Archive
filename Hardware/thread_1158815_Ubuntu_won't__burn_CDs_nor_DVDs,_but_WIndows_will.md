---
title: "Ubuntu won't  burn CDs nor DVDs, but WIndows will"
date: 2009-05-14
forum: Hardware
---

### Post by TBerk on 2009-05-14
Well, I have a dual boot system; Pent4 Dual Core @ 3GHz, (with only) 768M RAM, and two DVD-Rom drives. One reads the other is a read/write unit:

```



           *-cdrom:0
                description: DVD reader
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio dvd
                configuration: status=nodisc

           *-cdrom:1
                description: DVD-RAM writer
                product: DVDRAM GMA-4020B
                vendor: HL-DT-ST
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: A105
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc


```

If I boot in Wondows XP I can burn CDs & DVDs (reliably at slower than Max speeds) but Ubuntu won't burn at all.

It begins to prime the disk, but before it seems to actually get anywhere past 5% of data transfered, the disk spits out and the burn has failed.

The following seems to be the relevant portion of the error log when trying Brasero Burner app:

```

BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'HL-DT-ST'
BraseroWodim stdout: Identification : 'DVDRAM GMA-4020B'
BraseroWodim stdout: Revision       : 'A105'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0011 (DVD-R sequential recording)
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) (current)
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
BraseroWodim stdout: Driver flags   : SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: PACKET SAO
BraseroWodim stdout: Drive buf size : 1409024 = 1376 KB
BraseroWodim stdout: Drive DMA Speed: 11858 kB/s 67x CD 8x DVD
BraseroWodim stdout: FIFO size      : 33554432 = 32768 KB
BraseroWodim stderr: Speed set to 1385 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data  4388 MB        
BraseroWodim stdout: Total size:     5039 MB (499:16.08) = 2246706 sectors
BraseroWodim stdout: Lout start:     5039 MB (499:18/06) = 2246706 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
BraseroWodim stdout: Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 51790
BraseroWodim stdout: Starting to write CD/DVD at speed   1.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroGenisoimage stderr:   0.22% done, estimate finish Mon May 11 23:47:58 2009
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroGenisoimage stderr:   0.45% done, estimate finish Mon May 11 23:44:16 2009
BraseroGenisoimage stderr:   0.67% done, estimate finish Mon May 11 23:43:00 2009
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 00 00 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 0C 30 05 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.002s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:    0 of 4388 MB written.
BraseroWodim stdout: write track data: error after 0 bytes
BraseroWodim stdout: Writing  time:  100.289s
BraseroWodim stdout: Average write speed  36.9x.
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    0.010s
BraseroWodim stderr: wodim: fifo had 511 puts and 1 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim stdout: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroWodim
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
Session error : unknown (brasero_burn_record burn.c:2602)

```

Is there anything obvious that might help me to get Burning working on this system? (I do have an old HP 4x CDR around, but it of course won't do anything with DVD media...)


berk

---

### Post by utnubuuser on 2009-05-14
If I'm not mistaken, you have to install codec to burn DVDs.  Check threads on how to burn DVDs.  Might be through  the medibuntu repositories.
Your OS might think you're trying to burn DVDs because you've got DVD players, and not a CD player.

---

