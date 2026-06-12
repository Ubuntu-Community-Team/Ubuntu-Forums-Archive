---
title: "WIndows XP burns CDs but Ubuntu wont do any"
date: 2009-05-22
forum: Hardware
---

### Post by TBerk on 2009-05-22
Neither CD nor DVD burning will work in 9.04 (studio layed on as well).

I've tried Brasero, etc, etc. But as it stands I can only copy the file(s) over to the shared partition, dual boot back into XP and burn from there.

I have a P4 dual core and (only) 768M RAM, but plenty of hard drive space left. 

What might I adjust, install, update, configure to allow for useful CD/DVD buring in Ubuntu?

Thx,
TBerk

---

### Post by bagman817 on 2009-05-23
I'm having the same problem.  Able to make an ISO with K3B, K3B won't burn it.  Saw other threads recommending right clicking on ISO to write.  Tried unsuccessfully (DVD appears to burn completely, then errors out at the end).

Like poster above, ISO burns fine when copied to XP.  I was able to burn fine before upgrading to 9.04.  Any thoughts?

---

### Post by TBerk on 2009-09-01
Well, it's the end of August (with all attendant Synaptec managed Updates) and I'm bumping this thread to try it again.

I anticipate:

- Windows XP, Service Pack 3 with any app I choose (DeepBurner for example) will burn CDR and DVD-R disks, esp with pulled down, speed wise from MAX Burn Speed. 

- Ubuntu (Studio) 9.04 with Brasero, GnomeBaker, MPlayer "burn to disk", etc will start a CD or DVD burn but right near the end will end with an error.

Here is a sample log file from a failed attempt:


```

Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_DYM1XU.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_N790XU.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_5U20XU.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/xXxXxXx/movie/movie.iso (size = 51318784)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 14c40684afcdcfdee881e653346e79df ( before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_current_track
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/sr1
	speed=1
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/xXxXxXx/movie/movie.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.9
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
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
BraseroWodim stdout: Drive DMA Speed: 10716 kB/s 60x CD 7x DVD
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 1385 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data  4144 MB        
BraseroWodim stdout: Total size:     4760 MB (471:36.13) = 2122210 sectors
BraseroWodim stdout: Lout start:     4760 MB (471:38/10) = 2122210 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
BraseroWodim stdout: Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 176286
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
BraseroWodim stdout: Track 01:    0 of 4144 MB written.
BraseroWodim stdout: write track data: error after 0 bytes
BraseroWodim stdout: Writing  time:  101.662s
BraseroWodim stdout: Average write speed  34.9x.
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    0.014s
BraseroWodim stderr: wodim: fifo had 255 puts and 1 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2602)

```


Now, since then I've done some things with the OS; Removed and reinstalled 'gnome' desktop and 'smplayer' and other apps/utils inc Firefox 3.5, etc.

So, here we go- I'm gong to sacrifice another blank media (Maxell DVD-R 4.7GB 16x 2hr sp-mode) to see if anything has changed (bet it won't work In Ubuntu either...)

berk

---

### Post by TBerk on 2009-09-03
The news is not good; 

I have not been able to get 8.10 nor beta 9.04 nor released version 9.04 Ubuntu Studio to burn a CD nor DVD on a drive that WinXP will work well with.

What the frack?

I'm looking into having the hardware (DJLMS XJ-HD166S) up to date witht he latest bios, speaking of bios:

My cmos for the computer itself recognizes the drive w/ these parameters:

LBA Mode = Supported
PIO Mode = 4
UltraDMA = Mode 2
Cable = 80 pin conductor detected


I'm going to borrow an external (USB/Firewire) DVD burner to see if I can get something working...



berk

---

### Post by sprilutsky on 2009-09-08
Hi there,

Here is what I recommend you guys to try:

1. Open up a Brasero window, but do not do anything there yet
2. Open a File Browser 
3. Drag and drop a file/movie/song etc... from File borwser window into thr Brasero window and click on burn.


If you are burning avi fomrat, I recommend to download and install VLC movie [player, which plays Ubuntu burned avi files well on Windows XP.


Let me know if that worked or not

---

### Post by TBerk on 2009-09-12
> **sprilutsky said:**
> Hi there,

Here is what I recommend you guys to try:

1. Open up a Brasero window, but do not do anything there yet
2. Open a File Browser 
3. Drag and drop a file/movie/song etc... from File borwser window into the Brasero window and click on burn.


If you are burning avi fomrat, I recommend to download and install VLC movie [player, which plays Ubuntu burned avi files well on Windows XP.


Let me know if that worked or not


I'll try that but it's not particular to *what* I'm burning, all burns in Ubuntu OS fail, esp during the last 10%.  It can be an ISO file or a group of data files or authoring a DVD (w/ menus etc.)

I end up dropping  the 'to be burnt' output on an NTFS/FAT32 partition and reboot into WinXP. 

btw, I have VLC installed already. (I've been preferring SMPlayer though.)


berk

---

### Post by TBerk on 2009-11-01
OK, back w/ an update:

I installed 9.10 into a seperate, clean, aprtition. I retained my existing (built up in 9.04 Studio) '/Home partition though so thi smay be influencing the current results.

Just today/yesterday I got a Brasero update via auto-Update manager/Synaptics so I tried to burn some data CD-Rs.

no joy.

```

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_GBEB2U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage There is a checksum already 0
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_current_track
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/sr1
	speed=4
	fs=16m
	-data
	-nopad
	/media/4CD866EDD866D4AC/Arc/ubuntu-9.10-rc-desktop-i386.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: No write mode specified.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Asuming -tao mode.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Future versions of wodim may have different drive dependent defaults.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.9
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'HL-DT-ST'
BraseroWodim stdout: Identification : 'DVDRAM GMA-4020B'
BraseroWodim stdout: Revision       : 'A105'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1542912 = 1506 KB
BraseroWodim stdout: Drive DMA Speed: 7273 kB/s 41x CD 5x DVD
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 706 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   687 MB        
BraseroWodim stdout: Total size:      789 MB (78:12.14) = 351911 sectors
BraseroWodim stdout: Lout start:      789 MB (78:14/11) = 351911 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, high Beta category (A+) (3)
BraseroWodim stdout:   ATIP start of lead in:  -11634 (97:26/66)
BraseroWodim stdout:   ATIP start of lead out: 359846 (79:59/71)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 3
BraseroWodim stdout: Manufacturer: CMC Magnetics Corporation
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 7935
BraseroWodim stdout: Starting to write CD/DVD at speed   4.0 in real TAO mode for single session.
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
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of  687 MB written.
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 03 45 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 10 2A 30 02 80 21 02 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.002s timeout 40s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: The current problem looks like a buffer underrun.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: It looks like 'driveropts=burnfree' does not work for this drive.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please report.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Make sure that you are root, enable DMA and check your HW/OS set up.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:    1 of  687 MB written (fifo  99%) [buf  80%]   1.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 1714176 bytes
BraseroWodim stdout: Writing  time:   22.171s
BraseroWodim stdout: Average write speed 212.1x.
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:   63.750s
BraseroWodim stderr: wodim: fifo had 282 puts and 28 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 14 times full, min fill was 98%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

```

This is a dual boot system and I can burn CD/DVD media in WinXP (but some stuff and conditions req. I slow my BURN speed to x4).

So, still unable to burn CDs in Ubuntu. All for now.


berk
waiting a little while to re-start a bug report on this, I should 1st try and figure out just what I am reporting...

---

### Post by pavloukos on 2009-11-08
Had the same problem with an LG dvd-rw dl drive. I could not burn anything on a dvd using either brasero or gnomebaker although I successfully did in on xp.
I read some posts in this forum and tried cdrecord from the command line to burn an iso:

```

cdrecord -v speed=4 driveropts=burnfree dev=/dev/scd0 dvd.iso

```

and magically i did it ... don't know how. Before that I did a 

```

sudo chmod +s /usr/bin/wodim

```

i'm not sure if that command helped either.

Bottom line is that it worked.

---

### Post by Hominine on 2010-02-07
This works beautifully, thanks a lot!

---

