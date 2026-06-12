---
title: "Trying to make live CD"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by chkneater on 2009-10-25
Ok, I've DLed 9.04 and am using a blank CD-R.  

I've done the MMD5 bash check and verified the DL went OK.

When I try to burn it with the method described on Ubuntu.com, the burning doesn't finish.  I set the write speed for 8x which was the lowest allowed.  This is the log after I try to burn it:

Checking session consistency (brasero_burn_check_session_consistency burn.c:1956)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_854B2U.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_DY3B2U.bin toc = none
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
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_W68B2U.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/bobby/Desktop/ubuntu-9.04-desktop-i386.iso (size = 732909568)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 1) 66fa77789c7b8ff63130e5d5a272d67b ( before)
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
	dev=/dev/scd1
	gracetime=0
	speed=7
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/bobby/Desktop/ubuntu-9.04-desktop-i386.iso
BraseroWodim launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/scd1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.8
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stderr: wodim: Drive does not support SAO recording.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stderr: wodim: Try -raw option.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stderr: wodim: Illegal write mode for this drive.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 5
	message	= "The drive is busy"
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'PHILIPS '
BraseroWodim stdout: Identification : 'CDD4801 CD-R/RW '
BraseroWodim stdout: Revision       : 'C1.3'
BraseroWodim stdout: Device seems to be: Generic mmc CD-RW.
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC SWABAUDIO 
BraseroWodim stdout: Supported modes: TAO PACKET RAW/R16
BraseroWodim stdout: Drive buf size : 1572864 = 1536 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
Session error : The drive is busy (brasero_burn_record burn.c:2650)

---

### Post by stinger30au on 2009-10-25
i get wierd faults like this every then

i reboot the pc and try again and it works fine

hope that helps

---

### Post by vinutux on 2009-10-25
Try k3b

---

### Post by chkneater on 2009-10-26
Thanx, the K3b worked good.  I liked how it displayed the MD5.  It burned the CD good but now after installing 9.04 I get an error 18 just after the grub menu.

---

