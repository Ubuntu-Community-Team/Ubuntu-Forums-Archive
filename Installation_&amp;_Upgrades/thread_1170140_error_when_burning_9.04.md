---
title: "error when burning 9.04"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by orengolan on 2009-05-25
i get errors both on brasero and xfburn.
here is the log of brasero:

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_07WFUU.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_ES1FUU.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage Dummy operation, skipping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage Dummy operation, skipping
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
	dev=/dev/sr0
	-dummy
	speed=4
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/oren/xubuntu-9.04-desktop-i386.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
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
BraseroWodim stderr: Speed set to 706 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'HP      '
BraseroWodim stdout: Identification : 'DVD Writer 300n '
BraseroWodim stdout: Revision       : '1.25'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-ROM.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) (current)
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
BraseroWodim stdout: Drive buf size : 1345536 = 1314 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stdout: Track 01: data   616 MB        
BraseroWodim stdout: Total size:      708 MB (70:12.02) = 315902 sectors
BraseroWodim stdout: Lout start:      708 MB (70:14/02) = 315902 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type B, low Beta category (B-) (4)
BraseroWodim stdout:   ATIP start of lead in:  -12369 (97:17/06)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 69
BraseroWodim stdout: Manufacturer: Moser Baer India Limited
BraseroWodim stdout: Manufacturer is guessed because of the orange forum embargo.
BraseroWodim stdout: The orange forum likes to get money for recent information.
BraseroWodim stdout: The information for this media may not be correct.
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 43947
BraseroWodim stdout: Starting to write CD/DVD at speed   4.0 in dummy SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting dummy write in    4 seconds.
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
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of  616 MB written.
BraseroWodim stdout: Track 01:    1 of  616 MB written (fifo  98%) [buf 100%] 139.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of  616 MB written (fifo 100%) [buf 100%]   0.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   18 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   19 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   20 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   21 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   22 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   23 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   24 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   25 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   26 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   27 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   28 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   29 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   30 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   31 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   32 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   33 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   34 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   35 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   36 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   37 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   38 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   39 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   40 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   41 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   42 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   43 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   44 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   45 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   46 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   47 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   48 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   49 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   50 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   51 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   52 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   53 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   54 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   55 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   56 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   57 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   58 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   59 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   60 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   61 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   62 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   63 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   64 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   65 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   66 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   67 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   68 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   69 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   70 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   71 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   72 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   73 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   74 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   75 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   76 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   77 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   78 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   79 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   80 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   81 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   82 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   83 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   84 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   85 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   86 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   87 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   88 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   89 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   90 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   91 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   92 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   93 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   94 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   95 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   96 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   97 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   98 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   99 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  100 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  101 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  102 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  103 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  104 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  105 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  106 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  107 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  108 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  109 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  110 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  111 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  112 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  113 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  114 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  115 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  116 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  117 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  118 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  119 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  120 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  121 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  122 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  123 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  124 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  125 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  126 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  127 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  128 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  129 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  130 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  131 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  132 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  133 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  134 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  135 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  136 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  137 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  138 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  139 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  140 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  141 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  142 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  143 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  144 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  145 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  146 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  147 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  148 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  149 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  150 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  151 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  152 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  153 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  154 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  155 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  156 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  157 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  158 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  159 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  160 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  161 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  162 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  163 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  164 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  165 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  166 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  167 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  168 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  169 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  170 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  171 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  172 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  173 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  174 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  175 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  176 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  177 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  178 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  179 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  180 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  181 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  182 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  183 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  184 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  185 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  186 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  187 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  188 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  189 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  190 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  191 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  192 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  193 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  194 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  195 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  196 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  197 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  198 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  199 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  200 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  201 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  202 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  203 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  204 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  205 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  206 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  207 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  208 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  209 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  210 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  211 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  212 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  213 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  214 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  215 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  216 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  217 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  218 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  219 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  220 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  221 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  222 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  223 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  224 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  225 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  226 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  227 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  228 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  229 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  230 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  231 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  232 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  233 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  234 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  235 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  236 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  237 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  238 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  239 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  240 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  241 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  242 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  243 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  244 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  245 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  246 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  247 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  248 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  249 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  250 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  251 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  252 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  253 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  254 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  255 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  256 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  257 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  258 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  259 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  260 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  261 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  262 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  263 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  264 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  265 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  266 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  267 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  268 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  269 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  270 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  271 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  272 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  273 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  274 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  275 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  276 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  277 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  278 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  279 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  280 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  281 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  282 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  283 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  284 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  285 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  286 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  287 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  288 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  289 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  290 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  291 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  292 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  293 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  294 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  295 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  296 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  297 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  298 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  299 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  300 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  301 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  302 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  303 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  304 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  305 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  306 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  307 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  308 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  309 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  310 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  311 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  312 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  313 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  314 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  315 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  316 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  317 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  318 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  319 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  320 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  321 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  322 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  323 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  324 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  325 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  326 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  327 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  328 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  329 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  330 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  331 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  332 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  333 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  334 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  335 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  336 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  337 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  338 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  339 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  340 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  341 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  342 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  343 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  344 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  345 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  346 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  347 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  348 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  349 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  350 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  351 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  352 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  353 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  354 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  355 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  356 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  357 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  358 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  359 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  360 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  361 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  362 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  363 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  364 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  365 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  366 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  367 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  368 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  369 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  370 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  371 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  372 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  373 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  374 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  375 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  376 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  377 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  378 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  379 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  380 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  381 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  382 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  383 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  384 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  385 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  386 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  387 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  388 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  389 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  390 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  391 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  392 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  393 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  394 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  395 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  396 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  397 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  398 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  399 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  400 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  401 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  402 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  403 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  404 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  405 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  406 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  407 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  408 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  409 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  410 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  411 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  412 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  413 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  414 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  415 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  416 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  417 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  418 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  419 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  420 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  421 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  422 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  423 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  424 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  425 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  426 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  427 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  428 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  429 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  430 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  431 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  432 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  433 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  434 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  435 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  436 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  437 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  438 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  439 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  440 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  441 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  442 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  443 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  444 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  445 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  446 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  447 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  448 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  449 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  450 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  451 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  452 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  453 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  454 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  455 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  456 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  457 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  458 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  459 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  460 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  461 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  462 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  463 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  464 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  465 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  466 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  467 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  468 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  469 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  470 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  471 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  472 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  473 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  474 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  475 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  476 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  477 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  478 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  479 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  480 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  481 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  482 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  483 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  484 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  485 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  486 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  487 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  488 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  489 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  490 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  491 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  492 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  493 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  494 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  495 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  496 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  497 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  498 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  499 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  500 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  501 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  502 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  503 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  504 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  505 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  506 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  507 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  508 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  509 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  510 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  511 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  512 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  513 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  514 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  515 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  516 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  517 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  518 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  519 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  520 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  521 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  522 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  523 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  524 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  525 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  526 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  527 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  528 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  529 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  530 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  531 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  532 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  533 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  534 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  535 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  536 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  537 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  538 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  539 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  540 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  541 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  542 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  543 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  544 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  545 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  546 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  547 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  548 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  549 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  550 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  551 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  552 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  553 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  554 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  555 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  556 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  557 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  558 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  559 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  560 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  561 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  562 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  563 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  564 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  565 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  566 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  567 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  568 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  569 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  570 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  571 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  572 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  573 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  574 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  575 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  576 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  577 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  578 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  579 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  580 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  581 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  582 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  583 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  584 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  585 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  586 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  587 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  588 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  589 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  590 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  591 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  592 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  593 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  594 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  595 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  596 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  597 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  598 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  599 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  600 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  601 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  602 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  603 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  604 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  605 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  606 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  607 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  608 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  609 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  610 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  611 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  612 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  613 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  614 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  615 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  616 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01: Total bytes read/written: 646967296/646967296 (315902 sectors).
BraseroWodim stdout: Writing  time: 1094.135s
BraseroWodim stdout: Average write speed   3.8x.
BraseroWodim stdout: Min drive buffer fill was 100%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: WARNING: Some drives don't like fixation in dummy mode.
BraseroWodim stderr: wodim: fifo had 10191 puts and 10191 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating time:   25.710s
BraseroWodim stderr: wodim: fifo was 0 times empty and 9921 times full, min fill was 97%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: HUP
BraseroWodim stdout: HUP
BraseroWodim process finished with status 0
BraseroWodim called brasero_job_get_fd_out
BraseroWodim called brasero_job_get_action
BraseroWodim Finished successfully session
BraseroWodim stopping
BraseroWodim got killed
Dummy session successfully finished (brasero_burn_record_session burn.c:2090)
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_ML96TU.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_JX17TU.bin toc = none
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
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_N847TU.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/oren/xubuntu-9.04-desktop-i386.iso (size = 646967296)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 7afaff09c4b192415bad703ee564cff8 ( before)
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
	dev=/dev/sr0
	speed=4
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/oren/xubuntu-9.04-desktop-i386.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
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
BraseroWodim stdout: Vendor_info    : 'HP      '
BraseroWodim stdout: Identification : 'DVD Writer 300n '
BraseroWodim stdout: Revision       : '1.25'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-ROM.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) (current)
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
BraseroWodim stdout: Drive buf size : 1345536 = 1314 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 706 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   616 MB        
BraseroWodim stdout: Total size:      708 MB (70:12.02) = 315902 sectors
BraseroWodim stdout: Lout start:      708 MB (70:14/02) = 315902 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type B, low Beta category (B-) (4)
BraseroWodim stdout:   ATIP start of lead in:  -12369 (97:17/06)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 69
BraseroWodim stdout: Manufacturer: Moser Baer India Limited
BraseroWodim stdout: Manufacturer is guessed because of the orange forum embargo.
BraseroWodim stdout: The orange forum likes to get money for recent information.
BraseroWodim stdout: The information for this media may not be correct.
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 43947
BraseroWodim stdout: Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
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
BraseroWodim stdout: Track 01:    0 of  616 MB written.
BraseroWodim stdout: Track 01:    1 of  616 MB written (fifo  97%) [buf 100%]  97.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of  616 MB written (fifo 100%) [buf 100%]   0.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   18 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   19 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   20 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   21 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   22 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   23 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   24 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   25 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   26 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   27 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   28 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   29 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   30 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   31 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   32 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   33 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   34 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   35 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   36 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   37 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   38 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   39 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   40 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   41 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   42 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   43 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   44 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   45 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   46 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   47 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   48 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   49 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   50 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   51 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   52 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   53 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   54 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   55 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   56 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   57 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   58 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   59 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   60 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   61 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   62 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   63 of  616 MB written (fifo 100%) [buf 100%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   64 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   65 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   66 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   67 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   68 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   69 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   70 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   71 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   72 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   73 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   74 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   75 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   76 of  616 MB written (fifo 100%) [buf 100%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 9B 7C 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 03 00 00 98 E7 0A 00 00 00 00 0C 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x3 Medium Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 39143 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.138s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:   77 of  616 MB written (fifo 100%) [buf 100%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 81518592 bytes
BraseroWodim stdout: Writing  time:  180.186s
BraseroWodim stdout: Average write speed  23.7x.
BraseroWodim stdout: Min drive buffer fill was 100%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    0.001s
BraseroWodim stderr: wodim: fifo had 1539 puts and 1285 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: wodim: fifo was 0 times empty and 1270 times full, min fill was 97%.
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

---

### Post by Ripfox on 2009-06-03
Bump...this is happening to me too!!

---

### Post by whitefort on 2009-06-04
There seems to be a Brasero problem for some of us in Jaunty.  I had no problems on previous Ubuntus, and thought Brasero was great.

But in Jaunty it's only been good for turning blank DVDs into coffee-cup coasters.

Can't offer a solution as far as Brasero is concerned, but I've installed K3b, and it's been working perfectly.

---

### Post by kaefert66014235 on 2009-06-06
I just had the same problem with brasero.

```
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
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_85I1UU.md5
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
	-iso-level
	3
	-allow-limited-size
	-udf
	-graft-points
	-path-list
	/tmp/brasero_tmp_PRB7UU
	-exclude-list
	/tmp/brasero_tmp_2QB7UU
	-V
	Death Race 2008
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-quiet
	-print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 2282069
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
	dev=/dev/sr0
	speed=12
	driveropts=burnfree
	-dao
	fs=32m
	tsize=2282069s
	-data
	-nopad
	-
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage linked to BraseroWodim
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroChecksumImage
BraseroGenisoimage getting varg
BraseroChecksumImage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
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
	-iso-level
	3
	-allow-limited-size
	-udf
	-graft-points
	-path-list
	/tmp/brasero_tmp_3XVRUU
	-exclude-list
	/tmp/brasero_tmp_RJXRUU
	-V
	Death Race 2008
	-A
	Brasero-2.26.1
	-sysid
	LINUX
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: This size can only be represented in the UDF filesystem.
BraseroGenisoimage stderr: Make sure that your clients support and use it.
BraseroGenisoimage stderr: ISO9660, Joliet, RockRidge, HFS will display incorrect size.
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
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
BraseroWodim stdout: Vendor_info    : 'SONY    '
BraseroWodim stdout: Identification : 'DVD RW DRU-800A '
BraseroWodim stdout: Revision       : 'KY01'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0011 (DVD-R sequential recording)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) (current)
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
BraseroWodim stdout: Driver flags   : SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: PACKET SAO
BraseroWodim stdout: Drive buf size : 1563904 = 1527 KB
BraseroWodim stdout: FIFO size      : 33554432 = 32768 KB
BraseroWodim stderr: Speed set to 16620 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data  4457 MB        
BraseroWodim stdout: Total size:     5118 MB (507:07.58) = 2282069 sectors
BraseroWodim stdout: Lout start:     5119 MB (507:09/44) = 2282069 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
BraseroWodim stdout: Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 16427
BraseroWodim stdout: Starting to write CD/DVD at speed  13.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroGenisoimage stderr:   0.22% done, estimate finish Sat Jun  6 15:43:32 2009
BraseroGenisoimage stderr:   0.44% done, estimate finish Sat Jun  6 15:32:14 2009
BraseroGenisoimage stderr:   0.66% done, estimate finish Sat Jun  6 15:30:56 2009
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of 4457 MB written.
BraseroWodim stdout: Track 01:    1 of 4457 MB written (fifo  97%) [buf  84%]   0.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of 4457 MB written (fifo  97%) [buf  88%]   0.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of 4457 MB written (fifo  95%) [buf  99%]   6.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of 4457 MB written (fifo  92%) [buf  99%]   5.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of 4457 MB written (fifo  90%) [buf  99%]   5.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of 4457 MB written (fifo  87%) [buf  96%]   5.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of 4457 MB written (fifo  84%) [buf  99%]   5.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of 4457 MB written (fifo  81%) [buf  91%]   5.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of 4457 MB written (fifo  79%) [buf  99%]   5.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of 4457 MB written (fifo  77%) [buf  99%]   5.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of 4457 MB written (fifo  74%) [buf  98%]   5.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of 4457 MB written (fifo  71%) [buf  87%]   4.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:   0.88% done, estimate finish Sat Jun  6 18:15:46 2009
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 1B 9C 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: resid: 63488
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 26.206s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:   13 of 4457 MB written (fifo  68%) [buf  99%]   6.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: CDB:  00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: write track data: error after 14475264 bytes
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:  119.324s
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Average write speed  53.2x.
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Min drive buffer fill was 87%
BraseroWodim stderr: Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 1.495s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Trouble flushing the cache
BraseroWodim stderr: CDB:  35 00 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating time:    1.275s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 1.275s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot fixate disk.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 12
	message	= "An error occured while writing to disc"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroWodim
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
Session error : An error occured while writing to disc (brasero_burn_record burn.c:2599)

```

Stupidly I thought that maybe the blank disc was damaged, and tried it another time:

```
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
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_02R8UU.md5
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
	-iso-level
	3
	-allow-limited-size
	-udf
	-graft-points
	-path-list
	/tmp/brasero_tmp_NHW9UU
	-exclude-list
	/tmp/brasero_tmp_YYV9UU
	-V
	Death Race 2008
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-quiet
	-print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 2282069
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
	dev=/dev/sr0
	speed=12
	driveropts=burnfree
	-dao
	fs=32m
	tsize=2282069s
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
	-iso-level
	3
	-allow-limited-size
	-udf
	-graft-points
	-path-list
	/tmp/brasero_tmp_5D4UUU
	-exclude-list
	/tmp/brasero_tmp_UH4UUU
	-V
	Death Race 2008
	-A
	Brasero-2.26.1
	-sysid
	LINUX
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: This size can only be represented in the UDF filesystem.
BraseroGenisoimage stderr: Make sure that your clients support and use it.
BraseroGenisoimage stderr: ISO9660, Joliet, RockRidge, HFS will display incorrect size.
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
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
BraseroWodim stdout: Vendor_info    : 'SONY    '
BraseroWodim stdout: Identification : 'DVD RW DRU-800A '
BraseroWodim stdout: Revision       : 'KY01'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0011 (DVD-R sequential recording)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) (current)
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
BraseroWodim stdout: Driver flags   : SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: PACKET SAO
BraseroWodim stdout: Drive buf size : 1563904 = 1527 KB
BraseroWodim stdout: FIFO size      : 33554432 = 32768 KB
BraseroWodim stderr: Speed set to 16620 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data  4457 MB        
BraseroWodim stdout: Total size:     5118 MB (507:07.58) = 2282069 sectors
BraseroWodim stdout: Lout start:     5119 MB (507:09/44) = 2282069 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
BraseroWodim stdout: Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 16427
BraseroWodim stdout: Starting to write CD/DVD at speed  13.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroGenisoimage stderr:   0.22% done, estimate finish Sat Jun  6 18:24:09 2009
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroGenisoimage stderr:   0.44% done, estimate finish Sat Jun  6 18:16:37 2009
BraseroGenisoimage stderr:   0.66% done, estimate finish Sat Jun  6 18:14:04 2009
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of 4457 MB written.
BraseroWodim stdout: Track 01:    1 of 4457 MB written (fifo  97%) [buf  84%]   0.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of 4457 MB written (fifo  97%) [buf  99%]   0.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of 4457 MB written (fifo  96%) [buf  99%]   5.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of 4457 MB written (fifo  93%) [buf  98%]   5.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of 4457 MB written (fifo  91%) [buf  99%]   5.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of 4457 MB written (fifo  90%) [buf  99%]   5.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of 4457 MB written (fifo  88%) [buf  99%]   5.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of 4457 MB written (fifo  86%) [buf  98%]   5.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of 4457 MB written (fifo  84%) [buf  97%]   5.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of 4457 MB written (fifo  82%) [buf  98%]   5.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of 4457 MB written (fifo  81%) [buf  99%]   5.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of 4457 MB written (fifo  78%) [buf  99%]   5.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of 4457 MB written (fifo  77%) [buf  99%]   5.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of 4457 MB written (fifo  75%) [buf  99%]   5.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of 4457 MB written (fifo  72%) [buf  96%]   5.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of 4457 MB written (fifo  70%) [buf  99%]   5.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of 4457 MB written (fifo  68%) [buf  97%]   5.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:   0.88% done, estimate finish Sat Jun  6 20:52:33 2009
BraseroWodim stdout: Track 01:   18 of 4457 MB written (fifo  66%) [buf  99%]   5.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   19 of 4457 MB written (fifo  64%) [buf  99%]   5.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:   1.10% done, estimate finish Sat Jun  6 20:21:19 2009
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 28 15 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: resid: 63488
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 26.250s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:   20 of 4457 MB written (fifo  63%) [buf  88%]   4.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: CDB:  00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: write track data: error after 21014528 bytes
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:  117.903s
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Average write speed  54.7x.
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Min drive buffer fill was 88%
BraseroWodim stderr: Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.589s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Trouble flushing the cache
BraseroWodim stderr: CDB:  35 00 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating time:    1.597s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 1.597s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot fixate disk.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 12
	message	= "An error occured while writing to disc"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroWodim
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
Session error : An error occured while writing to disc (brasero_burn_record burn.c:2599)

```

I'm gonna take whiteforts advice and try it with K3b now..
If some developer of brasero is interested on more information, please say so. I always liked brasero best.

BTW, maybe this helps: Brasero works perfectly on another machine which is running Desktop 32bit version. The errors happend on an server 64bit installation (both 9.04)


EDIT: I just tried to run with simulation, this also failed (but fortunatly for my wallet already while simulating)

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_NFIZUU.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
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
	dev=/dev/sr0
	-dummy
	speed=6
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/kaefert/brasero.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
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
BraseroWodim stdout: Vendor_info    : 'SONY    '
BraseroWodim stdout: Identification : 'DVD RW DRU-800A '
BraseroWodim stdout: Revision       : 'KY01'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0011 (DVD-R sequential recording)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) (current)
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
BraseroWodim stdout: Driver flags   : SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: PACKET SAO
BraseroWodim stdout: Drive buf size : 1563904 = 1527 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 8310 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data  4457 MB        
BraseroWodim stdout: Total size:     5118 MB (507:07.58) = 2282069 sectors
BraseroWodim stdout: Lout start:     5119 MB (507:09/44) = 2282069 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
BraseroWodim stdout: Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 16427
BraseroWodim stdout: Starting to write CD/DVD at speed   6.0 in dummy SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting dummy write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of 4457 MB written.
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 03 C1 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: resid: 63488
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 26.626s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:    1 of 4457 MB written (fifo  99%) [buf  84%]   0.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 1968128 bytes
BraseroWodim stdout: Writing  time:   54.874s
BraseroWodim stdout: Average write speed  61.7x.
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: WARNING: Some drives don't like fixation in dummy mode.
BraseroWodim stderr: wodim: fifo had 286 puts and 32 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating time:    0.005s
BraseroWodim stderr: wodim: fifo was 0 times empty and 8 times full, min fill was 96%.
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

EDIT: I'm now using K3b, which works perfectly. However, I kinda liked that brasero added a textfile with the md5sum of the disc to the disc, which makes it easy to check if the disc is undamaged without having the files elsewhere for comparisons..

---

