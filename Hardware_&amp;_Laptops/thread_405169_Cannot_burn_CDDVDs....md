---
title: "Cannot burn CD/DVDs..."
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by accp-james on 2007-04-09
After installing Ubuntu 7.04 on my primary machine this weekend and being relatively pleased with it my next task was to get it installed on an older laptop that I use in the living room and the like for quick internet searches. Since the hardware is a bit antiquated I decided that I would be better off using Xubuntu so I donwloaded the iso and went to create the disc. Low and behold, I can't. 

> imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 16711 
	media type	= 0
	speed		= 56
	track type		= 8
	track format	= 2
	output		= none
job (BraseroCDRecord) set_rate
recorder (BraseroCDRecord) set_drive
recorder (BraseroCDRecord) set_flags
job (BraseroCDRecord) set_source
job (BraseroCDRecord) set_task
recorder (BraseroCDRecord) record
process (BraseroCDRecord) getting varg
process (BraseroCDRecord) got varg:
	cdrecord
	-v
	dev=/dev/scd1
	gracetime=0
	speed=56
iter (BraseroCDRecord) stopping
iter (BraseroCDRecord) stopped
job (BraseroCDRecord) set_task
Session error : unknown


This is the ouptut in the log from Brasero, but I haven't the faintest clue what it means. CD Burning worked out of the box for me with Fedora 6 and I have to confess that I've never burned CDs with Linux before last week, so I don't even know how the console based programs deal with the devices to do it.

I can tell you that I encounter the same issue with both my Philips DVD/RW DL and the TSSTCorp CDRW which are the only devices attached to the PATA controller on my Intel 945 express chipset based motherboard. My hard drives are both SATA. I'm idly wondering if Ubuntu is only installing the ATA driver or isn't installing SCSI emulation or some such...?

Anyway, help would be appreciated. The lack of CD burning and my mouse wheel not working (other post) are the only let downs I've had and I'm thoroughly convinced that they're probably easy fixes.

---

### Post by divague on 2007-04-09
try using another program to burn, like gnomebaker or k3b, gnomebaker works for me, but k3b is good too

---

### Post by accp-james on 2007-04-09
Sorry, I forgot to mention that I tried gnomebaker and one other that I can't remember off the top of my head. Same result. Mind you, it never actually tries to write to the disc, so it's not buffering problem or anything I'm familiar with from my Windows years. It's more like it can't access the write features of the drive.

---

