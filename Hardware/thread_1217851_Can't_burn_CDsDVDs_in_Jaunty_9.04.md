---
title: "Can't burn CDs/DVDs in Jaunty 9.04"
date: 2009-07-20
forum: Hardware
---

### Post by commbba on 2009-07-20
Hello,I'm having an Acer F3000 series laptop,based on an Acer Aspire 1450 platform laptops.The system runs Ubuntu 9.04 recently reinstalled and I'm doing all the available updates.
Now the problem is with the built-in CD/DVD recorder that can't burn any kind of disks.Not CDs,-r and -rw,neither DVDs.Also doesn't recognizes 3 audio cds that I bought despite that an Hi-Fi cd player plays them with no problem.The system's cd looks works good because I installed Ubuntu from there,recently.
I tried to burn CD-R,CD-RW and DVD-R with CD-DVD CREATOR,BRASERO & GNOMEBAKER,but all processes failed.Also the CDs that I'm inserting,is being recognized as CD-RW,a format that conflicts with audio-cd burnings.
After a little googling ,somewhere I saw that there is a problem with SATA controllers,as if I think that there is no SATA CD in the laptop,despite the Harddisk is being recognized as SATA HD.
I also found a bug report and fix but is for Intrepid and probably can't try it at Jaunty.
Here are the two log files BRASERO saved after data CD burning tries.
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
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_JJ9KXU.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
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
	/tmp/brasero_tmp_QL0AXU
	-exclude-list
	/tmp/brasero_tmp_7O0AXU
	-V
	Data disc (20 Jul 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-quiet
	-print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 180173
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage Finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage stopping
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_session_output_size
BraseroGenisoimage output set (IMAGE) image = /tmp/brasero_tmp_ZIAPXU.bin toc = none
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_image_output
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-path-list
	/tmp/brasero_tmp_IXAPXU
	-exclude-list
	/tmp/brasero_tmp_PKAPXU
	-V
	Data disc (20 Jul 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-o
	/tmp/brasero_tmp_ZIAPXU.bin
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr:   2.78% done, estimate finish Mon Jul 20 07:05:40 2009
BraseroGenisoimage stderr:   5.55% done, estimate finish Mon Jul 20 07:05:58 2009
BraseroGenisoimage stderr:   8.33% done, estimate finish Mon Jul 20 07:05:52 2009
BraseroGenisoimage stderr:  11.10% done, estimate finish Mon Jul 20 07:05:58 2009
BraseroGenisoimage stderr:  13.88% done, estimate finish Mon Jul 20 07:06:01 2009
BraseroGenisoimage stderr:  16.65% done, estimate finish Mon Jul 20 07:05:58 2009
BraseroGenisoimage stderr:  19.43% done, estimate finish Mon Jul 20 07:06:00 2009
BraseroGenisoimage stderr:  22.20% done, estimate finish Mon Jul 20 07:05:58 2009
BraseroGenisoimage stderr:  24.98% done, estimate finish Mon Jul 20 07:06:00 2009
BraseroGenisoimage stderr:  27.75% done, estimate finish Mon Jul 20 07:06:01 2009
BraseroGenisoimage stderr:  30.53% done, estimate finish Mon Jul 20 07:05:59 2009
BraseroGenisoimage stderr:  33.30% done, estimate finish Mon Jul 20 07:06:07 2009
BraseroGenisoimage stderr:  36.08% done, estimate finish Mon Jul 20 07:06:07 2009
BraseroGenisoimage stderr:  38.85% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  41.63% done, estimate finish Mon Jul 20 07:06:06 2009
BraseroGenisoimage stderr:  44.40% done, estimate finish Mon Jul 20 07:06:07 2009
BraseroGenisoimage stderr:  47.18% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  49.95% done, estimate finish Mon Jul 20 07:06:06 2009
BraseroGenisoimage stderr:  52.73% done, estimate finish Mon Jul 20 07:06:06 2009
BraseroGenisoimage stderr:  55.51% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  58.28% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  61.05% done, estimate finish Mon Jul 20 07:06:06 2009
BraseroGenisoimage stderr:  63.83% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  66.61% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  69.38% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  72.16% done, estimate finish Mon Jul 20 07:06:04 2009
BraseroGenisoimage stderr:  74.93% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  77.71% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  80.48% done, estimate finish Mon Jul 20 07:06:06 2009
BraseroGenisoimage stderr:  83.25% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  86.03% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  88.81% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  91.59% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  94.36% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stdout: HUP
BraseroGenisoimage stderr:  97.13% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr:  99.91% done, estimate finish Mon Jul 20 07:06:05 2009
BraseroGenisoimage stderr: Total translation table size: 0
BraseroGenisoimage stderr: Total rockridge attributes bytes: 1418
BraseroGenisoimage stderr: Total directory bytes: 4096
BraseroGenisoimage stderr: Path table size(bytes): 42
BraseroGenisoimage stderr: Max brk space used 0
BraseroGenisoimage stderr: 180173 extents written (351 MB)
BraseroGenisoimage stderr: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_output_type
BraseroGenisoimage called brasero_job_get_image_output
BraseroGenisoimage called brasero_job_add_track
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage Finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage stopping
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
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_OB2MXU.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /tmp/brasero_tmp_ZIAPXU.bin (size = 368994304)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 88e7de08d0e489e39e445c0af250607a ( before)
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
	speed=10
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/tmp/brasero_tmp_ZIAPXU.bin
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
BraseroWodim stdout: Vendor_info    : 'HL-DT-ST'
BraseroWodim stdout: Identification : 'DVD-RW GWA-4040N'
BraseroWodim stdout: Revision       : '1.01'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x000A (CD-RW)
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) (current)
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1308672 = 1278 KB
BraseroWodim stdout: Drive DMA Speed: 109342 kB/s 621x CD 78x DVD
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 1764 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Probably trying to use ultra high speed+ medium on improper writer.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   351 MB        
BraseroWodim stdout: Total size:      404 MB (40:02.30) = 180173 sectors
BraseroWodim stderr: wodim: fifo had 0 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Lout start:      404 MB (40:04/23) = 180173 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 0%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 0
BraseroWodim stdout:   Reference speed: 0
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is erasable
BraseroWodim stdout:   Disk sub type: Ultra High speed+ Rewritable media (3)
BraseroWodim stdout:   ATIP start of lead in:  -11075 (97:34/25)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout:   2T speed low:  8 2T speed high: 32
BraseroWodim stdout:   power mult factor: 0 0
BraseroWodim stdout:   recommended erase/write power: 0
BraseroWodim stdout:   A1 values: 00 00 80
BraseroWodim stdout:   A2 values: 39 80 00
BraseroWodim stdout:   A3 values: 00 00 00
BraseroWodim stdout: Disk type:    Phase change
BraseroWodim stdout: Manuf. index: 11
BraseroWodim stdout: Manufacturer: Mitsubishi Chemical Corporation
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 179676
BraseroWodim stdout: Writing  time:    3.959s
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2602)

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
BraseroBurnURI burn:// URI found burn:///%CE%A3%CE%AC%CE%B2%CE%B2%CE%B1%CF%82%20%CE%91%CE%BD%CE%B4%CF%81%CF%8C%CE%BD%CE%B9%CE%BA%CE%BF%CF%82
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///%CE%A3%CE%AC%CE%B2%CE%B2%CE%B1%CF%82%20%CE%91%CE%BD%CE%B4%CF%81%CF%8C%CE%BD%CE%B9%CE%BA%CE%BF%CF%82
BraseroBurnURI Adding directory (null) at /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Graft already in list /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/&#935;&#929;&#921;&#931;&#932;&#927;&#933;&#915;&#917;&#925;&#925;&#921;&#913;&#932;&#921;&#922;&#913;/
BraseroBurnURI Added file /media/Western Digital 160/&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/DORA.ppt at /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/DORA.ppt
BraseroBurnURI Added file /media/Western Digital 160/&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/PAIXNIDIA.ppt at /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/PAIXNIDIA.ppt
BraseroBurnURI Graft already in list /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/Photo Album.ppt
BraseroBurnURI Added file /media/Western Digital 160/&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/POTHRIA-PIATA.ppt at /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/POTHRIA-PIATA.ppt
BraseroBurnURI Added file /media/Western Digital 160/&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/Sxolika.ppt at /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/Sxolika.ppt
BraseroBurnURI Added file /media/Western Digital 160/&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/Sxolika_2.ppt at /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/Sxolika_2.ppt
BraseroBurnURI Added file /media/Western Digital 160/&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/TETRADIA.ppt at /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/TETRADIA.ppt
BraseroBurnURI Information retrieval for burn:///%CE%A3%CE%AC%CE%B2%CE%B2%CE%B1%CF%82%20%CE%91%CE%BD%CE%B4%CF%81%CF%8C%CE%BD%CE%B9%CE%BA%CE%BF%CF%82/Photo%20Album.ppt
BraseroBurnURI Added file /media/Western Digital 160/&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/Photo Album.ppt at /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/Photo Album.ppt
BraseroBurnURI Information retrieval for burn:///%CE%A3%CE%AC%CE%B2%CE%B2%CE%B1%CF%82%20%CE%91%CE%BD%CE%B4%CF%81%CF%8C%CE%BD%CE%B9%CE%BA%CE%BF%CF%82/%CE%A7%CE%A1%CE%99%CE%A3%CE%A4%CE%9F%CE%A5%CE%93%CE%95%CE%9D%CE%9D%CE%99%CE%91%CE%A4%CE%99%CE%9A%CE%91
BraseroBurnURI Adding directory (null) at /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/&#935;&#929;&#921;&#931;&#932;&#927;&#933;&#915;&#917;&#925;&#925;&#921;&#913;&#932;&#921;&#922;&#913;/
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Added file /media/Western Digital 160/&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/&#935;&#929;&#921;&#931;&#932;&#927;&#933;&#915;&#917;&#925;&#925;&#921;&#913;&#932;&#921;&#922;&#913;/Xristougeniatika.ppt at /&#931;&#940;&#946;&#946;&#945;&#962; &#913;&#957;&#948;&#961;&#972;&#957;&#953;&#954;&#959;&#962;/&#935;&#929;&#921;&#931;&#932;&#927;&#933;&#915;&#917;&#925;&#925;&#921;&#913;&#932;&#921;&#922;&#913;/Xristougeniatika.ppt
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
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_QUDSXU.md5
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
	/tmp/brasero_tmp_EJ4JXU
	-exclude-list
	/tmp/brasero_tmp_81RIXU
	-V
	Data disc (20 Jul 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-quiet
	-print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 180173
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
	speed=10
	driveropts=burnfree
	-dao
	fs=16m
	tsize=180173s
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
	/tmp/brasero_tmp_D66HXU
	-exclude-list
	/tmp/brasero_tmp_RA7HXU
	-V
	Data disc (20 Jul 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
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
BraseroWodim stdout: Vendor_info    : 'HL-DT-ST'
BraseroWodim stdout: Identification : 'DVD-RW GWA-4040N'
BraseroWodim stdout: Revision       : '1.01'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x000A (CD-RW)
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) (current)
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1308672 = 1278 KB
BraseroWodim stdout: Drive DMA Speed: 111227 kB/s 631x CD 80x DVD
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 1764 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Probably trying to use ultra high speed+ medium on improper writer.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   351 MB        
BraseroWodim stdout: Total size:      404 MB (40:02.30) = 180173 sectors
BraseroWodim stderr: wodim: fifo had 2 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Lout start:      404 MB (40:04/23) = 180173 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 0%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 0
BraseroWodim stdout:   Reference speed: 0
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is erasable
BraseroWodim stdout:   Disk sub type: Ultra High speed+ Rewritable media (3)
BraseroWodim stdout:   ATIP start of lead in:  -11075 (97:34/25)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout:   2T speed low:  8 2T speed high: 32
BraseroWodim stdout:   power mult factor: 0 0
BraseroWodim stdout:   recommended erase/write power: 0
BraseroWodim stdout:   A1 values: 00 00 80
BraseroWodim stdout:   A2 values: 39 80 00
BraseroWodim stdout:   A3 values: 00 00 00
BraseroWodim stdout: Disk type:    Phase change
BraseroWodim stdout: Manuf. index: 11
BraseroWodim stdout: Manufacturer: Mitsubishi Chemical Corporation
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 179676
BraseroWodim stdout: Writing  time:    3.963s
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 255
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

And here is GNOMEBAKER error logs after data CD burning tries

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RW GWA-4040N'
Revision       : '1.01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A (CD-RW)
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) (current)
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1308672 = 1278 KB
Drive DMA Speed: 113178 kB/s 643x CD 81x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 1764 KB/s
wodim: Probably trying to use ultra high speed+ medium on improper writer.
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 1 times full, min fill was 0%.

And after GNOMEBAKER data DVD burning tries


:-[ READ DISC INFORMATION failed with SK=3h/UNABLE TO RECOVER TABLE-OF-CONTENTS]: Input/output error


Sorry for the long post.

---

### Post by haiyun211 on 2009-07-22
Having similar problem with that same app mine does not give errors but just sits there saying that it is initializing  i think is the word.  I put gnome baker on to try and use something different and it said it was missing some kind of plug-in and I cant remember what the plug-in it said was.  Any help much apriciated.  Thanks in advance.

---

### Post by gaptekboy on 2009-07-22
Hi,

I am also facing the same problem. In my case, I have two DVD Burner, one is still using IDE (this one works fine) and the one which can't burn is using the SATA.

Does anybody have the solution?

---

### Post by chzumbrunnen on 2009-07-25
same here. Burning finishes with errors and sometimes "hangs".

---

### Post by gaptekboy on 2009-07-28
Hi, here's some update...

After a week of frustrating with Jaunty (I experienced annoying screen-lag & my DVD-RW won't burn CD), I decided to downgrade to Hardy Heron which I thought it's the best cause it's Long Term Support. Yeah, I have my problems fixed, but still my SATA DVD RW won't burn any DVD/CD.

It came up with these mesaages:

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1794)
Inconsistent flag: you can't use flag on_the_fly (brasero_burn_check_session_consistency burn.c:1892)
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=16
	-use-the-force-luke=tracksize:795776
	-use-the-force-luke=tty
	-Z
	/dev/scd1=/media/data3/Images/ridelikeapro.iso
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/media/data3/Images/ridelikeapro.iso of=/dev/scd1 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/scd1: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: /dev/scd1: reserving 795776 blocks
BraseroGrowisofs stderr: /dev/scd1: "Current Write Speed" is 16.4x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=4h/ASC=08h/ACQ=01h]: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2384)
```

Does anybody here know my real problem?

---

### Post by tardeevo on 2009-08-17
I'm having issues as well with my 2 pioneer burners (106D and 110D) both shiny working til ubuntu 8.10 - with the 110D I can't get to burn nothing so I stuck in the old 104D and I just had a couple of successful burns with sony DVD+R media but no luck with TDK DVD-Rs, go figure.
Anyhow this is another major disappointment to add to the pile of ... found on Jaunty - the worst distro I'd ever face in 10y of linux desktoppin' - and as a (former?) ubuntu enthusiast user I feel sad for the great work spent by the ubuntu dev community til before, possibly erased by this unfortunate son.

---

### Post by haiyun211 on 2009-08-17
Try using gnome baker that fixed all my problems.

---

