---
title: "Brasero"
date: 2008-07-16
forum: General Help
---

### Post by skiros on 2008-07-16
Hello, I'm having troubles with Brasero, normally I cant copy CD or DVD, only three times I could copy but now I cant copy any disk.

I have a report from brasero:

```

Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
Inconsistent flag: you can't use flag on_the_fly (brasero_burn_check_session_consistency burn.c:1810)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_N67WDU.bin toc = /tmp/brasero_tmp_N67WDU
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao getting varg
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao got varg:
BraseroCdrdao deactivating
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao getting varg
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_input_type
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao called brasero_job_get_device
BraseroCdrdao called brasero_job_get_flags
BraseroCdrdao called brasero_job_get_speed
BraseroCdrdao called brasero_job_get_flags
BraseroCdrdao called brasero_job_set_use_average_rate
BraseroCdrdao called brasero_job_set_current_action
BraseroCdrdao got varg:
	cdrdao
	write
	--device
	/dev/scd0
	-n
	-v
	2
	--speed
	18
	/home/skiros/Escritorio/brasero.toc
BraseroCdrdao launching command
BraseroCdrdao stderr: WARNING: Environment variable 'HOME' not defined - cannot read .cdrdao.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr:   SCSI interface library - (C) Joerg Schilling
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr:   Paranoia DAE library - (C) Monty
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Using libscg version 'ubuntu-0.8ubuntu1'
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: /dev/scd0: TOSHIBA DVDW/HD TS-L802A	Rev: TO35
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Starting write at speed 16...
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Process can be aborted with QUIT signal (usually CTRL-\).
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: WARNING: No super user permission to setup real time scheduling.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Turning BURN-Proof on
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Executing power calibration...
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Power calibration successful.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: cdrdao: Input/output error.  : scsi sendcmd: no error
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: CDB:  2A 00 FF FF FF 6A 00 00 1A 00
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: status: 0x2 (CHECK CONDITION)
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Sense Key: 0x3 Medium Error, Segment 0
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Sense flags: Blk 0 (not valid) 
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: cmd finished after 3.898s timeout 180s
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Write data failed.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Writing failed.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: HUP
BraseroCdrdao process finished with status 1
BraseroCdrdao called brasero_job_error
BraseroCdrdao finished with an error
BraseroCdrdao asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroCdrdao stopping
BraseroCdrdao got killed
Session error : unknown (brasero_burn_record burn.c:2273)

```

Thanks.

---

### Post by cetheriel on 2008-08-16
i have the same problem on my desktop, but can't find any help on ubuntuforums...

---

### Post by cmapesjr on 2008-08-16
Brasero only makes coasters for me as well.
I use k3b. Works just fine. :)

---

### Post by skiros on 2008-08-16
I have used k3b too and I have the same problem xD

Well... my "personal solution" is use my old pc (with "güindous") for copy cds and dvds...
Maybe with ubuntu 8.10 brasero works well.

---

### Post by editrix on 2008-08-17
There's a bug in Hardy that prevents many people from burning cds. Check out my post here: [http://ubuntuforums.org/showthread.php?t=884700](http://ubuntuforums.org/showthread.php?t=884700)
which also points to the bug on launchpad.

---

### Post by Crafty Kisses on 2008-08-17
I'd suggest k3b, try running "brasero" in Terminal and see what happens.

---

### Post by skiros on 2008-08-19
Ok, thank you, I will try it.

---

