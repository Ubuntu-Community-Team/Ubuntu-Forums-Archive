---
title: "Cannot create CD or DVD disks."
date: 2008-10-31
forum: General Help
---

### Post by michealPW on 2008-10-31
Hello,

I'm using Ubuntu 8.04 and I cannot burn any CDs or DVDs.
Regardless of which program I use, (They're clearly sharing the same broken component... Exactly why I left Windows!)

I did some research, found that the Debian Package Maintainers have replaced the Cdrtools package with a really buggy one. I instead downloaded the real package, replaced all the Wodim garbage with the real CDRTools, hoping it would solve my problems, which it didn't.

I still recieve an "unhandled error" from Nautilus and from Bresaro, although Bresaro at least displays SOME information:

```

BraseroMd5sum finished track successfully
BraseroMd5sum stopping
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
	-speed=1
	-use-the-force-luke=tracksize:358040
	-use-the-force-luke=tty
	-Z
	/dev/scd0=/storage/buffer/Kubuntu/kubuntu-8.10-desktop-i386.iso
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/storage/buffer/Kubuntu/kubuntu-8.10-desktop-i386.iso of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=3h/ASC=11h/ACQ=00h]: Input/output error
BraseroGrowisofs stderr: /dev/scd0: reserving 358040 blocks, warning for short DAO recording
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stdout:           0/733265920 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/733265920 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/733265920 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)

```

These errors occur typically immediately after the program attempts to write the CD, although sometimes Bresaro gets far enough to create a coaster, which I really appreciate, trust me.

---

### Post by michealPW on 2008-10-31
Also, I thought I might add something...

I read a little, and GrowISOFS seems to be for working with multi-session DVDs and CDs (CD-ReWritables, I suppose.)

My drive's labeled DVD+RW, and I'm using DVD-R media... Could it be that the system is not properly identifying the media, and attempting to write it as a multi-session DVD+RW instead of the DVD-R disk that it actually is?

In addition to that theory, why wouldn't any of these programs give me the option? Nautilus (The reason I'm attempting to try out Kubuntu....) is a peice of crap, and will not let me change any configuration options... But Bresaro I figured would and although it provides SOME customization, it says nothing about destination media etc.

---

### Post by meganox on 2008-10-31
This is extremely annoying, I can't even try to downgrade to Gutsy because I can't burn the install CD.  I can't switch to a distro that works because I can't burn an install CD... I'm stuck in Hardy Hell forever.

---

### Post by scottkicksbutt on 2009-01-26
I was having similar issues with intrepid even though I was able to burn dvd's with fedora9 on the same laptop several months ago.  I tried several different types of dvd media.  I have had no problems with cd's - just dvd's. I slowed down the burn speed from 8x to 4x and things appear to be working now.  The first dvd to burn successfully was windows7 beta which makes me feel a bit dirty...

System:
Thinkpad t60p using brasero to burn 

$ growisofs -version
* growisofs by <appro@fy.chalmers.se>, version 7.1,
  front-ending to genisoimage: genisoimage 1.1.8 (Linux)

$ uname -a
Linux t60-u08 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

---

