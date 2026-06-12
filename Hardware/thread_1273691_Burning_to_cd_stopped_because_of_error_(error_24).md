---
title: "Burning to cd stopped because of error (error 24)"
date: 2009-09-23
forum: Hardware
---

### Post by mjp29 on 2009-09-23
I have a list of mostly basic things to get Ubuntu to do for me, then I'll be convinced to do a total migration to Ubuntu (from old G4 Mac os X system).

Today, I decided to try to burn a cd.  I plugged up an external (fairly new) firewire/usb 2 cd/dvd burner and burn a cd with data on it.  I verified that my usb cord is usb 2 only by reading on side of usb cord it says that.  But the usb 2 cord i'm using is a long cord.

All appeared to be going well with dragging a folder (that had a small .mov file, a small .avi file, and one .jpg file in it) to the software that automatically opened when I inserted a blank cd.

All was going well until it informed me that the job had stopped and the data it burnt may be corrupt and the external drive ejected the cd.

Below is the message log (complete with errors). 



Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI burn:// URI found burn:///download%20folder
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///download%20folder
BraseroBurnURI Adding directory (null) at /download folder/
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Added file /home/michael/Desktop/download folder/P1040422.mov at /download folder/P1040422.mov
BraseroBurnURI Added file /home/michael/Desktop/download folder/MVI_1811.AVI at /download folder/MVI_1811.AVI
BraseroBurnURI Added file /home/michael/Desktop/download folder/P1010685.JPG at /download folder/P1010685.JPG
BraseroBurnURI no burn:// URI found
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_N9CK0U.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage deactivating
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-path-list
	/tmp/brasero_tmp_5XBJ0U
	-exclude-list
	/tmp/brasero_tmp_7GCJ0U
	-V
	Data disc (23 Sep 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-quiet
	-print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 5163
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage Finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_session_output_size
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/sr1
	speed=32
	driveropts=burnfree
	-dao
	fs=4m
	tsize=5163s
	-data
	-nopad
	-
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage linked to BraseroWodim
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroChecksumImage
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-path-list
	/tmp/brasero_tmp_R8AF0U
	-exclude-list
	/tmp/brasero_tmp_4DBF0U
	-V
	Data disc (23 Sep 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
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
BraseroWodim stdout: Version        : 0
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'PIONEER '
BraseroWodim stdout: Identification : 'DVD-RW  DVR-116D'
BraseroWodim stdout: Revision       : '1.03'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1136640 = 1110 KB
BraseroWodim stdout: FIFO size      : 4194304 = 4096 KB
BraseroWodim stderr: Speed set to 5644 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data    10 MB        
BraseroWodim stdout: Total size:       11 MB (01:08.84) = 5163 sectors
BraseroWodim stdout: Lout start:       11 MB (01:10/63) = 5163 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 4
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, low Beta category (A-) (2)
BraseroWodim stdout:   ATIP start of lead in:  -12508 (97:15/17)
BraseroWodim stdout:   ATIP start of lead out: 359845 (79:59/70)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 22
BraseroWodim stdout: Manufacturer: Ritek Co.
BraseroWodim stdout: Blocks total: 359845 Blocks current: 359845 Blocks remaining: 354682
BraseroWodim stdout: Starting to write CD/DVD at speed  32.0 in real SAO mode for single session.
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
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of   10 MB written.
BraseroWodim stdout: Track 01:    1 of   10 MB written (fifo  96%) [buf  97%]   0.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of   10 MB written (fifo 100%) [buf  89%]  15.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of   10 MB written (fifo 100%) [buf  90%]  17.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of   10 MB written (fifo  98%) [buf  92%]  16.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  96.98% done, estimate finish Wed Sep 23 17:21:54 2009
BraseroGenisoimage stderr: Total translation table size: 0
BraseroWodim stdout: Track 01:    5 of   10 MB written (fifo 100%) [buf  90%]  16.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr: Total rockridge attributes bytes: 727
BraseroGenisoimage stderr: Total directory bytes: 2048
BraseroGenisoimage stderr: Path table size(bytes): 26
BraseroGenisoimage stderr: Max brk space used 0
BraseroGenisoimage stderr: 5163 extents written (10 MB)
BraseroGenisoimage stderr: HUP
BraseroWodim stdout: Track 01:    6 of   10 MB written (fifo  98%) [buf  95%]  17.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage Finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroGenisoimage deactivating
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 79f392d8d73930369fc2fd14ff55c1c0 (file:///tmp/brasero_tmp_N9CK0U.md5 before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroWodim
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroChecksumImage deactivating
BraseroWodim stdout: Track 01:    7 of   10 MB written (fifo 100%) [buf  94%]  16.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of   10 MB written (fifo 100%) [buf  96%]  10.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of   10 MB written (fifo 100%) [buf  96%]  16.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of   10 MB written (fifo 100%) [buf  97%]  16.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01: Total bytes read/written: 10573824/10573824 (5163 sectors).
BraseroWodim stdout: Writing  time:   32.481s
BraseroWodim stdout: Average write speed   4.1x.
BraseroWodim stdout: Min drive buffer fill was 89%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    8.397s
BraseroWodim stderr: wodim: fifo had 167 puts and 167 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: wodim: fifo was 0 times empty and 36 times full, min fill was 81%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 0
BraseroWodim called brasero_job_get_fd_out
BraseroWodim called brasero_job_get_action
BraseroWodim Finished successfully session
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 10569728)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroReadom called brasero_job_get_action
BraseroReadom linked to BraseroChecksumImage
BraseroReadom getting varg
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroReadom reading 1 from sector 0 to 5161
BraseroReadom called brasero_job_get_fd_out
BraseroReadom called brasero_job_set_use_average_rate
BraseroReadom got varg:
	readom
	dev=/dev/sr1
	-nocorr
	-noerror
	-sectors=0-5161
	-f=-
BraseroReadom Launching command
BraseroReadom stderr: Read  speed:  7056 kB/s (CD  40x, DVD  5x).
BraseroReadom stderr: Write speed:  5644 kB/s (CD  32x, DVD  4x).
BraseroReadom stderr: Capacity: 5163 Blocks = 10326 kBytes = 10 MBytes = 10 prMB
BraseroReadom called brasero_job_set_current_action
BraseroReadom stderr: Sectorsize: 2048 Bytes
BraseroReadom stderr: Copy from SCSI (2,0,0) disk to file '-'
BraseroReadom stderr: end:      5161
BraseroReadom stderr: addr:        0 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:       60 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      120 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      180 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      240 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      300 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      360 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      420 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      480 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      540 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      600 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      660 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      720 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      780 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      840 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      900 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      960 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1020 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1080 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1140 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1200 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1260 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1320 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1380 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1440 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1500 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1560 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1620 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1680 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1740 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1800 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1860 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1920 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1980 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2040 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2100 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2160 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2220 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2280 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2340 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2400 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2460 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2520 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2580 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2640 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2700 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2760 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2820 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2880 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2940 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3000 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3060 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3120 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3180 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3240 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3300 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3360 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3420 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3480 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3540 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3600 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3660 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3720 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3780 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3840 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3900 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3960 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4020 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4080 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4140 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4200 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4260 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4320 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4380 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4440 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4500 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4560 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4620 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4680 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4740 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4800 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4860 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4920 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4980 cnt: 60
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5040 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5100 cnt: 60

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5160 cnt: 1
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5161
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: Time total: 10.473sec
BraseroReadom stderr: Read 10322.00 kB at 985.6 kB/sec.
BraseroReadom stderr: HUP
BraseroReadom process finished with status 0
BraseroReadom called brasero_job_get_fd_out
BraseroReadom Finished track successfully
BraseroReadom got killed
BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage
BraseroReadom deactivating
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 8d7e49ded571b8d398f2cc835f94dfbf (79f392d8d73930369fc2fd14ff55c1c0 before)
BraseroChecksumImage called brasero_job_error
BraseroChecksumImage finished with an error
BraseroChecksumImage asked to stop because of an error
	error		= 24
	message	= "Some files may be corrupted on the disc"
BraseroChecksumImage stopping
BraseroChecksumImage closing connection for BraseroChecksumImage
Session error : Some files may be corrupted on the disc (brasero_burn_record burn.c:2599)

---

