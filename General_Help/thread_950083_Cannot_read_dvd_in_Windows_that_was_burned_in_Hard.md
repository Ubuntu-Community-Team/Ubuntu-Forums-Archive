---
title: "Cannot read dvd in Windows that was burned in Hardy"
date: 2008-10-16
forum: General Help
---

### Post by ThaAllGood1 on 2008-10-16
First off let me mention that everytime, ok about 90% of the time I burn a dvd using Brasero I ends (at 99%) with an error.  If it was a movie ISO it will play in my DVD player no problem.  I would like to know how to resolve this error as it is annoying.  

The bigger concern is if it is a data disk it cannot be read in windows.  I have tried to read it on multiple computers using windows and multiple running Hardy, some dual boots others as a VM.  I know it is not hardware as i can read it in Hardy reboot or load the VM and not read it in Windows.  I think the the issue goes back to the issue above with the error messages when burning at 99% complete.

Please Help and TIA.

---

### Post by Sam on 2008-10-16
Have you tried to burn at lower speed ?


Can we have a look to the error messages ?

---

### Post by ThaAllGood1 on 2008-10-17
Burning at 1x it errored out at 99%, below is the log file.  

Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile deactivating
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_set_current_action
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_add_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile finished track successfully
BraseroMd5sumFile stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=2
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-dry-run
	-r
	-J
	-iso-level
	3
	-udf
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_7XKUIU
	-exclude-list
	/tmp/brasero_tmp_361UIU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -iso-level 3 -udf -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_7XKUIU -exclude-list /tmp/brasero_tmp_361UIU -print-size | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 1393714
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
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
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=2
	-use-the-force-luke=tracksize:1393714
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-r
	-J
	-iso-level
	3
	-udf
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_Y5O6IU
	-exclude-list
	/tmp/brasero_tmp_M4O6IU
	-V
	Data disc (16 Oct 08)
	-A
	Brasero-0.7.1
	-sysid
	LINUX
	-v
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: genisoimage 1.1.6 (Linux)
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -iso-level 3 -udf -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_Y5O6IU -exclude-list /tmp/brasero_tmp_M4O6IU -V Data disc (16 Oct 08) -A Brasero-0.7.1 -sysid LINUX -v | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Scanning /home/austin/Desktop/Maya 2008
BraseroGrowisofs stderr: Scanning /home/austin/Desktop/Maya 2008/Crack
BraseroGrowisofs stderr: Scanning /home/austin/Desktop/Sony.Sound.Forge.v9.0e
BraseroGrowisofs stderr: Scanning /home/austin/Desktop/Sony.Sound.Forge.v9.0e/NoPE
BraseroGrowisofs stderr: Scanning /home/austin/Desktop/FruityLoops Studio 8.0 XXL Edition
BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet Volume Descriptor                Start Block 17
BraseroGrowisofs stderr: Done with: Joliet Volume Descriptor                Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 18
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   UDF volume recognition area             Start Block 19
BraseroGrowisofs stderr: Done with: UDF volume recognition area             Block(s)    3
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 22
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   UDF pad to sector 32                    Start Block 23
BraseroGrowisofs stderr: Done with: UDF pad to sector 32                    Block(s)    9
BraseroGrowisofs stderr: Writing:   UDF main seq                            Start Block 32
BraseroGrowisofs stderr: Done with: UDF main seq                            Block(s)    16
BraseroGrowisofs stderr: Writing:   UDF second seq                          Start Block 48
BraseroGrowisofs stderr: Done with: UDF second seq                          Block(s)    16
BraseroGrowisofs stderr: Writing:   UDF integ seq                           Start Block 64
BraseroGrowisofs stderr: Done with: UDF integ seq                           Block(s)    2
BraseroGrowisofs stderr: Writing:   UDF pad to sector 256                   Start Block 66
BraseroGrowisofs stderr: Done with: UDF pad to sector 256                   Block(s)    190
BraseroGrowisofs stderr: Writing:   UDF Anchor volume                       Start Block 256
BraseroGrowisofs stderr: Done with: UDF Anchor volume                       Block(s)    1
BraseroGrowisofs stderr: Writing:   UDF file set                            Start Block 257
BraseroGrowisofs stderr: Done with: UDF file set                            Block(s)    2
BraseroGrowisofs stderr: Writing:   UDF directory tree                      Start Block 259
BraseroGrowisofs stderr: Done with: UDF directory tree                      Block(s)    12
BraseroGrowisofs stderr: Writing:   UDF file entries                        Start Block 271
BraseroGrowisofs stderr: Done with: UDF file entries                        Block(s)    12
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 283
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Joliet path table                       Start Block 287
BraseroGrowisofs stderr: Done with: Joliet path table                       Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 291
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    6
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 297
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    6
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 303
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 303
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 304
BraseroGrowisofs stderr:   0.36% done, estimate finish Thu Oct 16 20:28:16 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   0.72% done, estimate finish Thu Oct 16 20:30:35 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   1.08% done, estimate finish Thu Oct 16 20:31:21 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-RW DAO upon user request...
BraseroGrowisofs stderr: /dev/scd0: reserving 1393714 blocks
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 2.0x1352KBps.
BraseroGrowisofs stderr:   1.44% done, estimate finish Thu Oct 16 20:56:08 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   1.79% done, estimate finish Thu Oct 16 20:54:16 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
.
.
.
BraseroGrowisofs stderr:  98.30% done, estimate finish Thu Oct 16 20:45:33 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  98.66% done, estimate finish Thu Oct 16 20:45:33 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  99.02% done, estimate finish Thu Oct 16 20:45:34 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  99.38% done, estimate finish Thu Oct 16 20:45:33 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  99.73% done, estimate finish Thu Oct 16 20:45:33 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: Total translation table size: 0
BraseroGrowisofs stderr: Total rockridge attributes bytes: 2287
BraseroGrowisofs stderr: Total directory bytes: 10240
BraseroGrowisofs stderr: Path table size(bytes): 124
BraseroGrowisofs stderr: Done with: The File(s)                             Block(s)    1393259
BraseroGrowisofs stderr: Writing:   UDF Anchor end volume                   Start Block 1393563
BraseroGrowisofs stderr: Done with: UDF Anchor end volume                   Block(s)    1
BraseroGrowisofs stderr: Writing:   UDF Pad end                             Start Block 1393564
BraseroGrowisofs stderr: Done with: UDF Pad end                             Block(s)    150
BraseroGrowisofs stderr: Max brk space used 0
BraseroGrowisofs stderr: 1393714 extents written (2722 MB)
BraseroGrowisofs stderr: :-[ WRITE@LBA=154430h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)

---

### Post by ThaAllGood1 on 2008-10-25
Still needing help,  I think i have may found some of the cause but not sure of the rsolution.  Looks to be an issue when i burn a file over 2gb to a disk, ie a ISO file.  This is a dual boot with XP and XP has no issues burning the same data.

---

### Post by LDRoamer on 2008-10-30
I am having the same problem. DVD's burned in Ubuntu Hardy are unreadable on Windows. No solution but you are not alone. Its not my burner as I dual boot windows on this machine and have no trouble creating discs in Windows.

---

### Post by monkeyking on 2008-10-31
how much memory do you have?

---

### Post by LDRoamer on 2008-10-31
I am not the original poster but if your asking me I have 512 mb of ram. The computer is an older Compaq desktop with a 1.9 ghz Pentium 4. After some googling it seems I am not the only one having this problem with Hardy. If anyone can suggest a fix that would be great. I may try 8.10 to see if the fixes things up.

> **monkeyking said:**
> how much memory do you have?

---

### Post by monkeyking on 2008-11-01
Is this a problem with all burns, og just brasero?

---

### Post by malty on 2008-11-01
Both Nero 3 and K3b will give flawless dvd burning of both data and video files playable on winows(XP3) 
Are you using other apps or surfing whilst burning, if so, don't. I would use either of the above before Brasero

---

### Post by ThaAllGood1 on 2008-11-01
Sorry for the delay, I have 1GB in my sysytem.  It does not matter if other apps are running in the back ground or not.  I have upgraded to 8.10 on still having the same issue but now with a little twist.  When the burn fails I cannot eject the disk.  If i push the button nothing happens, if i right click on the drive and select Eject i get the errors.

error 1:  Unable to mount drive

Error 2  UNable to eject the cd-rw/dvd +-RW Drive
 DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was

---

### Post by russlar on 2008-11-01
this sounds like a brasero bug. try a different burner. k3b is generally reliable.

---

### Post by LDRoamer on 2008-11-03
I have tried K3b and still it does not work. It appears to complete okay but when I try to read it in windows the disk shows no files but it also states that all the space on the DVD is used. I can read the disk in Ubuntu but neither XP nor Vista will read teh disc. On my XP box it actually causes explorer to crash.

---

### Post by n0tmycupoftea on 2008-11-13
I too was experiencing this problem and it drove me up the wall! But after LOTS of digging I found out that Hardy has a buggy genisoimage package. The solution? To downgrade to gutsy's genisoimage package found here: [http://packages.ubuntu.com/gutsy/genisoimage]("http://packages.ubuntu.com/gutsy/genisoimage")

Scroll down and select the correct genisoimage package for your system. Afterwards, in the terminal go to where you had saved the deb file and do the following:

1. sudo dpkg --force-downgrade -i genisoimage_1.1.6-1ubuntu3_"architecture".deb

2. since you downgraded ubuntu will want you to upgrade it and bug you every single time so to avoid this, go into your synaptic manager as root and locate genisoimage. click on the package tab and then click lock version and you should be set.

Here's the whole thread in which this was discussed, [http://ubuntuforums.org/showthread.php?t=787299&page=2]("http://ubuntuforums.org/showthread.php?t=787299&page=2"),I threw up what worked for me here so you wouldn't have to delve into numerous pages, but the thread itself isn't all that bad only 6pgs.

Goodluck!

---

