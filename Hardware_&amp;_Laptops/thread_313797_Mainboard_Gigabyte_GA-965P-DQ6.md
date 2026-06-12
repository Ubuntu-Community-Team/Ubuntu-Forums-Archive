---
title: "Mainboard Gigabyte GA-965P-DQ6"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by klemi on 2006-12-06
Hi,

i will buy the Mainboard Gigabyte GA-965-DQ6.

Can I install Ubuntu Edgy Eft 6.10?
Have someone do this with this Board?

The interals:
Chipsatz

Intel P965
Southbridge 	Intel 82801HR (ICH8R)

On-Board Controller
 	Audio 	Realtek ALC888DD
 	IDE (P-ATA) 	1 x ATA/100 für 2 Geräte
 	LAN 	Marvell 8053
 	RAID 	Intel ICH8R SATA RAID
 	S-ATA 	6 x SATA 300 via Southbridge

Thank you very much for comments

Klemi

---

### Post by RandallC on 2006-12-10
I have this board.  I have yet to figure out how to get audio working, otherwise it all works fine.  Does anyone know how to make audio work?

---

### Post by mjaker on 2006-12-11
> **klemi said:**
> Hi,

i will buy the Mainboard Gigabyte GA-965-DQ6.

Can I install Ubuntu Edgy Eft 6.10?
Have someone do this with this Board?

The interals:
Chipsatz

Intel P965
Southbridge 	Intel 82801HR (ICH8R)

On-Board Controller
 	Audio 	Realtek ALC888DD
 	IDE (P-ATA) 	1 x ATA/100 für 2 Geräte
 	LAN 	Marvell 8053
 	RAID 	Intel ICH8R SATA RAID
 	S-ATA 	6 x SATA 300 via Southbridge

Thank you very much for comments

Klemi

I just got the GA-965P-GS and it more or less works for me with Edgy 6.10.  The audio just worked...  The built in ethernet controller does not, there are posts for that topic: [http://ubuntuforums.org/showthread.php?t=297743](http://ubuntuforums.org/showthread.php?t=297743)
My system occasionally hangs on the boot process, I'm not sure what that's about...

Not sure what the DQ6 vs S3 diff is but like I said, most of the stuff works for me.  I've got a Nvidia 7950 GT KO video card, SATA drives.  Good luck!

---

### Post by jomiz80 on 2007-02-05
I have this board as well.  Here are some impressions:

1_audio-out does work. 
2_ audio-in (or microphone) does not work
3_ ethernet does not work
4_ system hangs occasionally on shut-down or restart


Otherwise, it seems to work pretty good!  I'll post a follow-up if I can get the microphone to work. (I need Skype, dang-it!)

---

### Post by jomiz80 on 2007-03-07
Ok, so I have the GA-965P-S3 and Edgy Eft 6.10

I got **audio-out** to work by following the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=272166&page=2&highlight=microphone](http://ubuntuforums.org/showthread.php?t=272166&page=2&highlight=microphone)
Also, for Skype to work, I had to change the settings to use the ALSA drivers. After that a quick reboot, and it works!

On-board ethernet still does not work, but I've hooked up a Zonet ZEW2501 (ZD1211b) b/g wifi dongle a few problems to get it to work, but works nonetheless!

The system hang was fixed by turning off UPS support (can't find the thread right now, sorry).

---

