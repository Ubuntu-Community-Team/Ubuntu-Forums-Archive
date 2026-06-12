---
title: "Mounted CD-ROM Icon with no cd in drive"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by cristianrosa on 2007-11-05
I have done a Ubuntu Gutsy clean install on my system, and i'm having the following issue.
When i login, I have a mounted cd-rom icon in my desktop, but there is no cdrom in the drive itself, and sometimes it opens sound juicer because it detects it is an audio CD!
The system has 2 drives, a dvd-rw and a cd-rom drive. They are detected as hda and hdb (the hard disk is sda1). 
If i try to use the cd-rom drive, when i insert a CD (ie. ubuntu 7.10) and double click the desktop icon, i get the nautilus cd burner window!
One more tip, up to edgy the drives worked fine, but since feisty i am having this issue. I thought it was an issue of having upgraded from edgy to feisty, but now that i did a clean install i am still having the problem.

---

### Post by AegisTalons on 2007-11-20
Yea, I'm having the same issue but it doesn't stop at the DVD/CD-ROM drive but also my USB drives and my IPOD. If anyone knows what the issue is, please let me know.

---

### Post by Krovas on 2007-11-21
Make that three. I came home to find the mounted phantom audio disk, and now Feisty thinks every disk i put in the tray is an audio disk.

---

### Post by Krovas on 2007-11-21
Here, does this clue anybody in? This resulted from my last attempt at reading a cd:

```


dmesg | tail

[36159.398693] ide: failed opcode was: unknown
[36159.398697] hda: drive not ready for command
[36159.445654] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[36159.445663] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[36159.445667] ide: failed opcode was: unknown
[36159.399952] hda: error code: 0x70  sense_key: 0x05  asc: 0x21  ascq: 0x00
[36159.399958] end_request: I/O error, dev hda, sector 4194368
[36159.401352] isofs_fill_super: bread failed, dev=hda, iso_blknum=1048592, block=2097184
[36161.434501] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[36171.226543] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```


Does this sound like a software failure or hardware? Just as a side note, my thumb drives are mounting normally. 

I do hope somebody has a clue; this inability to read cds is a very vexing problem.

---

### Post by Krovas on 2007-11-21
Okay, everything is back to normal after a cold boot, so this is a software hiccup of some sort.

---

### Post by gwpritch on 2007-11-22
I have the same issue. It seemed to resolve with a reboot but then the icon just re-appeared on the desktop without warning.

---

### Post by Krovas on 2007-11-24
Okay, I take it we're all on laptops? What kind? Compaq (Hewlett Packard) Presario F700 here.

---

### Post by wribeiro on 2007-11-26
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=466000](http://ubuntuforums.org/showthread.php?t=466000) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the same issue here.
I have a Medion Life Notebook, AMD Athlon 1.8 MHz, 512MB RAM, CD/DVD RW, ATI Radeon 1280x800, Ubuntu 7.10
The first time I installed Ubuntu 7.1 on the same computer, a few weeks ago, it didnt happen.
Now, some minutes after login, appears a "ghost" Audio CD Icon on my desktop and a Error Message from Sound Juicer: "can not read track list" "track numbers must be within 1..99"
But the cd drive is empty!!
After this, I can't eject the drive anymore.
I found another post about the same problem:
[http://ubuntuforums.org/showthread.php?t=466000](http://ubuntuforums.org/showthread.php?t=466000)
Thank you.

---

### Post by Krovas on 2008-02-24
*bump* This problem is persistent and irritating.

---

