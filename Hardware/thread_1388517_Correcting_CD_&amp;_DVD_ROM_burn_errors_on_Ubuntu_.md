---
title: "Correcting CD &amp; DVD ROM burn errors on Ubuntu 9.04"
date: 2010-01-23
forum: Hardware
---

### Post by Nightstrike2009 on 2010-01-23
I have a problem with recording with both CD/DVD Writers on my machine one is IDE one SATA.

In a book I have on Ubuntu 8.04 and above (My Ubuntu is 9.04) and I read these instructions:
> To Activate burnproof technology on Ubuntu, open a terminal window an type "gconf-editor". When the window opens click Edit>Find then type "Burnproof". Ensuring that there is a tick in "Search also key names", then click "Find" .In the search results at the bottom of the window, click the result (/apps/nautilus-cd-burner/bunrproof) and check "Burnproof" at the top right of the window. Then close the configuration editor.

I can get to > When the window opens click Edit>Find then type "Burnproof". Ensuring that there is a tick in "Search also key names", then click "Find"

But at this point I get an error window with "Pattern not found" in configuration editor.

Can anyone help on this?

---

### Post by Nightstrike2009 on 2010-01-23
I have heard of people enabling burnproof on Ubuntu Karmic 9.10, with gconf-editor, could one of you please post an how to on this thread? 


It may help me even though I am on Ubuntu 9.04 Jaunty.

PS: I left Karmic has it recognised my 3G modem and set it up but would not connect, I use it to connect to the internet, it works on 9.04 without 9.04 I wouldn't be able to connect to the net at all.

---

### Post by Nightstrike2009 on 2010-01-23
Brasero burn errors:

> Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
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
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_Y67R6U.md5
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
	/tmp/brasero_tmp_GD6Y6U
	-exclude-list
	/tmp/brasero_tmp_EZ6Y6U
	-V
	Virtualbox Back Up
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-quiet
	-print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 25448
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
	tsize=25448s
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
	/tmp/brasero_tmp_4OWN6U
	-exclude-list
	/tmp/brasero_tmp_UPWN6U
	-V
	Virtualbox Back Up
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
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'PIONEER '
BraseroWodim stdout: Identification : 'DVD-RW  DVR-115D'
BraseroWodim stdout: Revision       : '1.18'
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
BraseroWodim stdout: Drive buf size : 1267712 = 1238 KB
BraseroWodim stdout: FIFO size      : 4194304 = 4096 KB
BraseroWodim stderr: Speed set to 5644 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data    49 MB        
BraseroWodim stdout: Total size:       57 MB (05:39.30) = 25448 sectors
BraseroWodim stdout: Lout start:       57 MB (05:41/23) = 25448 sectors
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
BraseroWodim stdout: Blocks total: 359845 Blocks current: 359845 Blocks remaining: 334397
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
BraseroWodim stdout: Track 01:    0 of   49 MB written.
BraseroWodim stdout: Track 01:    1 of   49 MB written (fifo  98%) [buf  97%]   0.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of   49 MB written (fifo  98%) [buf  94%]  15.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of   49 MB written (fifo  98%) [buf  97%]  17.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of   49 MB written (fifo  98%) [buf  94%]  15.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  19.70% done, estimate finish Sat Jan 23 14:39:43 2010
BraseroWodim stdout: Track 01:    5 of   49 MB written (fifo  96%) [buf  98%]  18.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of   49 MB written (fifo 100%) [buf  92%]  10.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of   49 MB written (fifo  98%) [buf  96%]  17.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of   49 MB written (fifo  98%) [buf  93%]  15.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of   49 MB written (fifo  96%) [buf  98%]  17.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of   49 MB written (fifo  98%) [buf  94%]  15.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of   49 MB written (fifo  96%) [buf  99%]  17.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of   49 MB written (fifo 100%) [buf  96%]  15.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of   49 MB written (fifo 100%) [buf  87%]  15.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of   49 MB written (fifo 100%) [buf  91%]  16.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  39.32% done, estimate finish Sat Jan 23 14:38:27 2010
BraseroWodim stdout: Track 01:   15 of   49 MB written (fifo  98%) [buf  94%]  17.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of   49 MB written (fifo 100%) [buf  92%]  15.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of   49 MB written (fifo  98%) [buf  96%]  17.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   18 of   49 MB written (fifo  98%) [buf  93%]  15.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   19 of   49 MB written (fifo  96%) [buf  98%]  17.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   20 of   49 MB written (fifo  98%) [buf  95%]  15.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   21 of   49 MB written (fifo  96%) [buf  99%]  17.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   22 of   49 MB written (fifo 100%) [buf  96%]  15.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   23 of   49 MB written (fifo 100%) [buf  88%]  15.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   24 of   49 MB written (fifo  96%) [buf  98%]  18.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  59.00% done, estimate finish Sat Jan 23 14:38:02 2010
BraseroWodim stdout: Track 01:   25 of   49 MB written (fifo 100%) [buf  90%]  15.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   26 of   49 MB written (fifo 100%) [buf  87%]  15.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   27 of   49 MB written (fifo 100%) [buf  91%]  17.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   28 of   49 MB written (fifo 100%) [buf  89%]  15.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   29 of   49 MB written (fifo  98%) [buf  94%]  17.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   30 of   49 MB written (fifo 100%) [buf  91%]  15.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   31 of   49 MB written (fifo  98%) [buf  95%]  17.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   32 of   49 MB written (fifo  98%) [buf  92%]  15.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   33 of   49 MB written (fifo 100%) [buf  89%]  15.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   34 of   49 MB written (fifo  98%) [buf  94%]  18.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  78.62% done, estimate finish Sat Jan 23 14:37:49 2010
BraseroWodim stdout: Track 01:   35 of   49 MB written (fifo 100%) [buf  91%]  15.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   36 of   49 MB written (fifo  98%) [buf  96%]  17.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   37 of   49 MB written (fifo  98%) [buf  92%]  15.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   38 of   49 MB written (fifo  96%) [buf  97%]  11.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   39 of   49 MB written (fifo  98%) [buf  94%]  15.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   40 of   49 MB written (fifo  96%) [buf  99%]  17.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   41 of   49 MB written (fifo  98%) [buf  96%]  15.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   42 of   49 MB written (fifo 100%) [buf  88%]  15.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   43 of   49 MB written (fifo  96%) [buf  98%]  18.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  98.27% done, estimate finish Sat Jan 23 14:37:42 2010
BraseroWodim stdout: Track 01:   44 of   49 MB written (fifo 100%) [buf  88%]  15.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr: Total translation table size: 0
BraseroGenisoimage stderr: Total rockridge attributes bytes: 2189
BraseroGenisoimage stderr: Total directory bytes: 6144
BraseroGenisoimage stderr: Path table size(bytes): 62
BraseroGenisoimage stderr: Max brk space used 0
BraseroGenisoimage stderr: 25448 extents written (49 MB)
BraseroGenisoimage stderr: HUP
BraseroWodim stdout: Track 01:   45 of   49 MB written (fifo  96%) [buf  98%]  18.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage Finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroGenisoimage deactivating
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 3506b2d62dafaa0d2d8c5671e48aaa36 (file:///tmp/brasero_tmp_Y67R6U.md5 before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroWodim
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroChecksumImage deactivating
BraseroWodim stdout: Track 01:   46 of   49 MB written (fifo 100%) [buf  90%]  15.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   47 of   49 MB written (fifo 100%) [buf  87%]  15.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   48 of   49 MB written (fifo 100%) [buf  92%]  17.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   49 of   49 MB written (fifo 100%) [buf  89%]  15.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01: Total bytes read/written: 52117504/52117504 (25448 sectors).
BraseroWodim stdout: Writing  time:   47.342s
BraseroWodim stdout: Average write speed  10.2x.
BraseroWodim stdout: Min drive buffer fill was 87%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    8.139s
BraseroWodim stderr: wodim: fifo had 821 puts and 821 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: wodim: fifo was 0 times empty and 321 times full, min fill was 81%.
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
BraseroReadom called brasero_job_get_action
BraseroReadom linked to BraseroChecksumImage
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_trackBraseroReadom getting varg

BraseroReadom called brasero_job_get_action
BraseroChecksumImage called brasero_job_set_current_action
BraseroReadom called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_fd_in
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroChecksumImage Starting checksum generation live (size = 52113408)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_inBraseroReadom reading 1 from sector 0 to 25446

BraseroChecksumImage called brasero_job_get_fd_out
BraseroReadom called brasero_job_get_fd_out
BraseroReadom called brasero_job_set_use_average_rate
BraseroReadom got varg:
	readom
	dev=/dev/sr1
	-nocorr
	-noerror
	-sectors=0-25446
	-f=-
BraseroReadom Launching command
BraseroReadom called brasero_job_get_fd_in
BraseroReadom called braser: Track 01:   45 of   49 MB written (fifo  96%) [buf  98%]  18.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage Finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroGenisoimage deactivating
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 3506b2d62dafaa0d2d8c5671e48aaa36 (file:///tmp/brasero_tmp_Y67R6U.md5 before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroWodim
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroChecksumImage deactivating
BraseroWodim stdout: Track 01:   46 of   49 MB written (fifo 100%) [buf  90%]  15.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   47 of   49 MB written (fifo 100%) [buf  87%]  15.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   48 of   49 MB written (fifo 100%) [buf  92%]  17.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   49 of   49 MB written (fifo 100%) [buf  89%]  15.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01: Total bytes read/written: 52117504/52117504 (25448 sectors).
BraseroWodim stdout: Writing  time:   47.342s
BraseroWodim stdout: Average write speed  10.2x.
BraseroWodim stdout: Min drive buffer fill was 87%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    8.139s
BraseroWodim stderr: wodim: fifo had 821 puts and 821 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: wodim: fifo was 0 times empty and 321 times full, min fill was 81%.
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
BraseroReadom called brasero_job_get_action
BraseroReadom linked to BraseroChecksumImage
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_trackBraseroReadom getting varg

BraseroReadom called brasero_job_get_action
BraseroChecksumImage called brasero_job_set_current_action
BraseroReadom called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_fd_in
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroChecksumImage Starting checksum generation live (size = 52113408)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_inBraseroReadom reading 1 from sector 0 to 25446

BraseroChecksumImage called brasero_job_get_fd_out
BraseroReadom called brasero_job_get_fd_out
BraseroReadom called brasero_job_set_use_average_rate
BraseroReadom got varg:
	readom
	dev=/dev/sr1
	-nocorr
	-noerror
	-sectors=0-25446
	-f=-
BraseroReadom Launching command
BraseroReadom stderr: Read  speed:  7056 kB/s (CD  40x, DVD  5x).
BraseroReadom stderr: Write speed:  5644 kB/s (CD  32x, DVD  4x).
BraseroReadom stderr: Capacity: 25448 Blocks = 50896 kBytes = 49 MBytes = 52 prMB
BraseroReadom called brasero_job_set_current_action
BraseroReadom stderr: Sectorsize: 2048 Bytes
BraseroReadom stderr: Copy from SCSI (6,1,0) disk to file '-'
BraseroReadom stderr: end:     25446
BraseroReadom stderr: addr:        0 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:       64 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      384 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      512 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      704 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      832 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:      960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1024 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1152 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1536 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1664 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1856 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     1984 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2112 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2240 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2752 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     2944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3264 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3904 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     3968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4608 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     4992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5312 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     5952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6016 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     6976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7424 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     7936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8896 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     8960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9600 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9728 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:     9984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10304 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10432 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    10944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11072 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11200 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11776 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    11968 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12480 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12736 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    12992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13248 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13504 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    13952 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14272 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14720 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    14976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15040 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15488 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15808 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    15936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16192 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16576 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    16960 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17344 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17408 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17472 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17536 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17600 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17664 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17728 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17792 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17856 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17920 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    17984 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18048 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18112 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18176 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18240 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18304 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18368 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18432 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18496 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18560 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18624 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18688 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18752 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18816 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18880 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    18944 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19008 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19072 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19136 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19200 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19264 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19328 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19392 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19456 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19520 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19584 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19648 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19712 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19776 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19840 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19904 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    19968 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20032 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20096 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20160 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20224 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20288 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20352 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20416 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20480 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20544 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20608 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20672 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20736 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20800 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20864 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20928 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    20992 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21056 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21120 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21184 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21248 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21312 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21376 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21440 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21504 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21568 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21632 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21696 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21760 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21824 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21888 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    21952 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22016 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22080 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22144 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22208 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22272 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22336 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22400 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22464 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22528 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22592 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22656 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22720 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22784 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22848 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22912 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    22976 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23040 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23104 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23168 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23232 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23296 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23360 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23424 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23488 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23552 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23616 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23680 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23744 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23808 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23872 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    23936 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24000 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24064 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24256 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24320 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24384 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24448 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24512 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24576 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24640 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24704 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24768 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24832 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24896 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    24960 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25024 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25088 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25152 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25216 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25280 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25344 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25408 cnt: 38
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: addr:    25446
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: Time total: 23.983sec
BraseroReadom stderr: Read 50892.00 kB at 2122.0 kB/sec.
BraseroReadom stderr: HUP
BraseroReadom process finished with status 0
BraseroReadom called brasero_job_get_fd_out
BraseroReadom Finished track successfully
BraseroReadom got killed
BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage
BraseroReadom deactivating
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 0a2a791e89aa590362c5c38824fe1497 (3506b2d62dafaa0d2d8c5671e48aaa36 before)
BraseroChecksumImage called brasero_job_error
BraseroChecksumImage finished with an error
BraseroChecksumImage asked to stop because of an error
	error		= 24
	message	= "Some files may be corrupted on the disc"
BraseroChecksumImage stopping
BraseroChecksumImage closing connection for BraseroChecksumImage
Session error : Some files may be corrupted on the disc (brasero_burn_record burn.c:2599)


---

### Post by Nightstrike2009 on 2010-01-26
LOL I guess you want a job done properly then do it yourself eh?

I've just downloaded and installed the excellent "Gnomebaker 0.6.4" I can now burn discs in Ubuntu no problem. (Must have been Brasero faulty)

Anyhow thats the solution install gnomebaker and use that instead. :-)

---

