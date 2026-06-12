---
title: "Can't burn an iso to cd using Hardy"
date: 2008-09-16
forum: Hardware
---

### Post by barsofham on 2008-09-16
I'm trying to burn an iso for xubuntu to a cd but I keep getting error messages. When I try to burn it using the old "right click on iso then click Burn to Disc" trick, it tells me to insert a blank or compatible CD. But it doesn't matter what CD I use, I get the same message. I've tried brasero and it gave me this error log
```

Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
Inconsistent flag: you can't use flag on_the_fly (brasero_burn_check_session_consistency burn.c:1810)
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum output set (IMAGE) image = /tmp/brasero_tmp_8UP1HU toc = (null)
BraseroMd5sum called brasero_job_get_session_output_size
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum called brasero_job_set_current_action
BraseroMd5sum called brasero_job_start_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum setting new checksum 665bcc283e131be4cb71ecb2bf0e3794 ((null) before)
BraseroMd5sum finished track successfully
BraseroMd5sum stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_DX6NHU toc = (null)
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action

BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
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
	dev=/dev/scd0
	gracetime=0
	speed=28
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/devin/Linux Distros/xubuntu-8.04-desktop-i386.iso
BraseroWodim launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.6
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
BraseroWodim stdout: Vendor_info    : 'MATSHITA'
BraseroWodim stdout: Identification : 'UJ-832D         '
BraseroWodim stdout: Revision       : '1.00'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO
BraseroWodim stdout: Drive buf size : 1310720 = 1280 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 4234 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   544 MB        
BraseroWodim stdout: Total size:      625 MB (61:57.02) = 278777 sectors
BraseroWodim stdout: Lout start:      625 MB (61:59/02) = 278777 sectors
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
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 81069
BraseroWodim stdout: Starting to write CD/DVD at speed  24.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in  0 seconds. Operation starts.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stderr: Errno: 5 (Input/output error), send opc scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  54 01 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:    8.044s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 15 12 73 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: Sense Key: 0x3 Medium Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 8.020s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: OPC failed.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo had 255 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2273)

```

Thanks for any help you can give. Sorry for such a long error log.

---

### Post by phidia on 2008-09-16
Googling some of the errors in your output provided this [bug]("https://bugs.launchpad.net/ubuntu/+bug/227886"), and the thread [here]("http://ubuntuforums.org/showthread.php?t=788890") that mentions that bug.

I don't think that's the entire picture and I also don't know what you can do in the meantime.

Here are the [hits]("http://www.google.com/search?q=BraseroWodim+called+brasero_job_set_dangerous&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a") my search generated.

---

### Post by barsofham on 2008-09-17
Thanks, at least I know it's not just a problem with my hardware. Maybe I can just stick it out a month and hopefully Intrepid does a better job.

---

### Post by stchman on 2008-09-17
Install K3b, it burns .iso files well.

```
sudo apt-get -y install k3b libk3b2-extracodecs
```

---

### Post by mickey46834 on 2008-10-02
Same problem here, I can burn DVDs but I have a whole stack of CD-R Music cd's and when K3B does the OPC it pops the cd out and says maybe you should try a different media. Well I tried another cd and it didn't work either. Does Ubuntu not like to use Music cd's? Because I can use regular cd's ok. Didn't think there was much of a difference between the data and music cd's also tried brasero and same thing.

---

### Post by SuperSonic4 on 2008-10-02
Aren't music CD-Rs already written and thus not blank media though?

I've never used Brasero (never used ubuntu) but k3b does all my burning needs, I managed to get arch burned ok

---

### Post by mickey46834 on 2008-10-02
> **SuperSonic4 said:**
> Aren't music CD-Rs already written and thus not blank media though?

I've never used Brasero (never used ubuntu) but k3b does all my burning needs, I managed to get arch burned ok

I was talking blank Music cd's as in I went to the store and bought blank Music CD-R instead of Data CD-R's now I have 100 blank new Music CD-R that I can't seem to burn on.

---

