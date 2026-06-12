---
title: "CDs don't finish burning, appear again as blank"
date: 2010-07-13
forum: Hardware
---

### Post by benplaut on 2010-07-13
Having this issue in both Brasero and k3b, in user and in sudo.  When I try to burn a data CD, at the end of burn process the program will display a general error (one time I got a specific error from k3b, could not fixate).

When I remove the CD and put it back in the system, it appears as blank.  Reading CDs works fine.  Looking at the CD by eye, data has been written to the disk.

Matshita DVD-RAM UJ-842, in a Thinkpad T60. CD's are likely not the problem, several tested and with other computers, and the drive has worked in past Ubuntu releases.

Dmesg is full of errors identical to this:
```
[188849.874664] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[188849.874669] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[188849.874674] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[188849.874680] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[188849.874690] end_request: I/O error, dev sr0, sector 0
```

Mahalo!  8-)

---

### Post by whoboo on 2010-07-21
I have exactly the same problem.   It's very annoying when the OS can't deliver basic services like CD writing, reliably ... or at all.

---

### Post by whoboo on 2010-07-22
bump

---

### Post by whoboo on 2010-07-22
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stderr: Errno: 5 (Input/output error), read track info scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:    7.437s
BraseroWodim stderr: CDB:  52 01 00 00 00 FF 00 00 1C 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Average write speed 999.0x.
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.001s timeout 240s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot get next writable address for 'invisible' track.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: This means that we are checking recorded media.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: This media cannot be written in streaming mode anymore.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot get next writable address.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating time:   42.604s
BraseroWodim stderr: wodim: fifo had 64 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
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
BraseroWodim closing connection for BraseroWodim
Session error : unknown (brasero_burn_record brasero-burn.c:2842)

-------------------------

using TDK CD-R music/audio
I can write data to these OK on HP laptop.
I can read them on the CD-ROM that won't write.

---

### Post by wkulecz on 2010-07-22
Broken for me too!

Same hardware is fine if I multi-boot back into 6.06 or 8.04.

Terrible black-eye for 10.04 IMHO.

---

### Post by qQChtIhpk1 on 2010-08-01
i have same problem with 10.04 - can't burn an iso image to CD with Brasero, GnomeBaker or Wodim.  Even spent $19.95 on Nero ver 4 and have the same problem.  10.04 makes coasters of CD-RWs, since they can't be read by Nero - Unsupported Format.  

Please, this is Serious!  Thank You for your help.

Chazbo

---

### Post by Manyette on 2010-08-03
Just to add to the confusion, I too have this problem.  Specifically, I am not able to burn ISO files, while I can sometimes write other types, but not always.  For me this problem started with some update in 9.10, although I can't be sure which one.  It has continued through a fresh install of 10.04, and happens with Brasero, and K3B.  All of these worked find on the same machines (one HP and one Acer) prior to that 9,10 update.  Since I rarely use CD/DVD burning for anything other than ISO's, I'm not really too sure of what other functions have broken.

---

### Post by Manyette on 2010-08-04
To add to my previous post, I have loaded 9.04 in a spare partition, and the ISO burning function works perfectly on the same machine which fails with 10.04.  If it is of any help, that version uses wodim 1.1.9 and the 2.6.28-11 kernel. If there is any further information or tests which I could perform to help, I would be glad to do so.

---

### Post by ciciel on 2010-08-06
According to the thread [http://ubuntuforums.org/showthread.php?t=1167212]("http://ubuntuforums.org/showthread.php?t=1167212") the following command should help.

```
sudo chmod +s /usr/bin/wodim
```

I tried it and it worked.

I hope it helps.

---

### Post by pwebster25 on 2010-08-11
I tried running that command but I still get the same bad results in Brasero.

---

