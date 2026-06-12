---
title: "sata dvd burner troubles"
date: 2010-03-06
forum: Hardware
---

### Post by goodmanbrown on 2010-03-06
I put a new Serial ATA DVD burner (an LG GH22) in my computer, and it's causing me a couple kinds of trouble.

#1.  It rips audio CDs, but it does it very slowly.  It takes about 20 minutes to rip a normal CD.  That's up from 4 or 5 minutes with my old IDE CD-ROM.  It' the sort of thing I used to see with IDE drives when DMA wasn't enabled by default.  But from reading around a bit, it looks like DMA isn't a concern in the SATA world.

#2.  It won't burn successfully.  It does write enough data to the disc to make a coaster, but it won't finish a burn either in Brasero or Xfburn.  Xfburn gives the error:

```
** (xfburn:5734): WARNING **: [FATAL] 131357: SCSI error on write(-7,13): [5 30 05]  Cannot write medium, incompatible format (0)

** (xfburn:5734): WARNING **: [FATAL] 131339: Burn run failed (0)
```

The output of wodim -checkdrive is:

```
desktop:~$ wodim -checkdrive
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GH22NS50 '
Revision       : 'TN01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
```

It's not a permissions problem, because I get the same errors running as root.

I'm running a fresh install of 64-bit Karmic.

Any advice about where to begin would be great.  I've never tried an SATA optical drive before, and it's been so long since I had any hardware troubles with Ubuntu, my trouble-shooting skills have pretty much disappeared.

---

### Post by goodmanbrown on 2010-03-07
A little more information.  I have no idea how to parse this.  I tried to burn a mix CD with Brasero, and this is the tail end of log file it generated.  

```
BraseroWodim stdout: Total size:      769 MB (76:14.60) = 343095 sectors
BraseroWodim stdout: Lout start:      769 MB (76:16/45) = 343095 sectors
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
BraseroWodim stdout: Blocks total: 359845 Blocks current: 359845 Blocks remaining: 16750
BraseroWodim stdout: Starting to write CD/DVD at speed  48.0 in dummy SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting dummy write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 FF FF F9 24 00 02 A0 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: SAO startsec: -12508
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing lead-in...
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 0A 2A 00 00 80 30 05 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: write CD-Text data: error after 1032192 bytes
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:   15.929s
BraseroWodim stderr: Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.002s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Could not write Lead-in.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 15
	message	= "An error occured while writing to disc"
BraseroWodim stopping
BraseroWodim got killed
Session error : An error occured while writing to disc (brasero_burn_record brasero-burn.c:2808)
```

Also, after Brasero fails, a dialog box pops up that says, "Unable to mount Audio Disc.  Drive /dev/sr0 does not contain audio files."  I don't know what's popping up that message, or why, but it doesn't seem to be Brasero.  (The dialog box hangs around after I've closed Brasero down.)

---

### Post by goodmanbrown on 2010-03-08
And another tidbit, though I doubt this has anything to do with the drive.  I tried installing Gnomebaker, and it crashes before I can try burning. Sometimes it crashes while I'm adding files, sometimes when I click the burn button. Just now it crashed while I was selecting files to add, with this error:

```
(gnomebaker:14039): GLib-WARNING **: g_set_prgname() called multiple times
*** glibc detected *** gnomebaker: corrupted double-linked list: 0x0000000001166ef0 ***
```

---

### Post by carlosbellino on 2010-03-26
Hi, try cheking that you DVD-writer have "pata_atiixp driver" with
command "[FONT=monospace]dmesg | grep scsi[0-7]"[/FONT]
__________________________________________________  _______________________
[FONT=monospace]kaname@kaname-desktop:~$ dmesg | grep scsi[0-7]
[    1.274677] scsi0 : ahci
[    1.274727] scsi1 : ahci
[    1.274757] scsi2 : ahci
[    1.274785] scsi3 : ahci
[COLOR=Red][    1.275092] scsi4 : pata_atiixp
[    1.275120] scsi5 : pata_atiixp[/COLOR]
[    2.079988] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.379864] scsi6 : SCSI emulation for USB Mass Storage devices
__________________________________________________  ________________________

Sata Channels 4 and 5 have it,
Verify where is your burner:
"dmesg | grep scsi | grep GH22NS50"

[/FONT][FONT=monospace]__________________________________________________  ________________________

kaname@kaname-desktop:~$ dmesg | grep scsi | grep GH22NS50
[    2.058836] [COLOR=Red]scsi 2[/COLOR]:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
[/FONT][FONT=monospace]__________________________________________________  ________________________
[/FONT]
[FONT=monospace]and [/FONT]then at the mobo plug the SATA cable on 4th or 5th sata channel..

---

### Post by drtvasudevan on 2010-03-31
a little confused.
just yesterday i got the same model dvd drive and as it was not working i searched and came here.

as per your instructions:

> drtv@narayana:~$ dmesg | grep scsi[0-7]
[    0.660361] scsi0 : ahci
[    0.660472] scsi1 : ahci
[    0.660555] scsi2 : ahci
[    0.660610] scsi3 : ahci
[    0.660672] scsi4 : ahci
[    0.660732] scsi5 : ahci
[    0.661498] scsi6 : pata_marvell
[    0.661567] scsi7 : pata_marvell
[    1.775062]  sda1 sda2 < sda5sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
drtv@narayana:~$ wodim -checkdrive
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GH22NS50 '
Revision       : 'TN02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
drtv@narayana:~$ dmesg | grep scsi | grep GH22NS50
[    1.765620] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
drtv@narayana:~$ 



may be i am missing something but there are only 4 sata ports i can attach the sata cable to. earlier i was using a PATA dvd drive and using the lone PATA port.
mobo is intel 965

pl guide me.

---

### Post by suniyo on 2010-04-10
I'm having the same problem with the LG super multi SATA dvd writer drive. Did anyone found the solution? Stops after burning about 20% (almost always) and gives same error as stated here.

---

### Post by suniyo on 2010-04-21
I think this has something to do with the kernel in ubuntu few people reported that it worked well after upgrade to 10.04 I have not tried it yet and it is still not working. 

Any Developments here?

---

### Post by Professor Bear on 2010-10-05
:neutral: I'll offer my most recent findings... Not great news...

The IDE DVD writer on my web server gave out a few days back, so I went and got a new 'cheapy' LG SATA drive. HD on the server is SATA anyways, so why not? Server runs 8.04 LTS Server... No joy. System sees it as a DVD Read Only device. Tried the permissions changes recommended in some of the threads, still no joy. In fact, spent most all day yesterday fooling around with it.

Hey wait a minute! My workstation runs Ubuntu 10.04 LTS Desktop... It has a SATA DVD writer (Lenovo branded)... I've never tried it out for writing DVDs. No joy there as well. Well slap me and call me Susan. SATA DVD burners don't work except as a DVD reader?!?!? At least not with kernel 2.6.32.25... I was going to try some old kernel images, but got sidetracked, as one will on 'vacation'.

During the side-tracking, happened across an Asus IDE DVD writer in one of my parts boxes... Installed it in the server and it worked with no setup at all. It just worked.

For the workstation, my "electronics nut" friend made me am IDE to SATA card. Connected the Lenovo branded DVD writer using an IDE port on the mainboard, through the converter board, to the SATA port on the drive. Works.

Sort of strange to me that the dev's seem to be giving it "an ignore it and it will go away" attitude, but that may just be my perception. If any dev is reading this, may I suggest that there be a re-focus on the idea of making it an OS for the masses? The masses may not have friends that are electronics nuts.

Just some thoughts.

Edit: SATA DVD writer does not work on my BSD box either. Sorry dev's, it looks like a kernel issue...

---

