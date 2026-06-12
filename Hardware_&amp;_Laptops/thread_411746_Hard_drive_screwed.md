---
title: "Hard drive screwed?"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by Nesnej Trick on 2007-04-17
I was doing some 3D work in blender when I heard a click from my HDD, followed by the familiar grinding search noise hard drives make. Then Blender froze completely. Kooldock was working though, so I opened konsole and tried to kill blender, which didn't react, so I resorted to: sudo shutdown -r now

However, the system wouldn't apparently shut down completely due to this:
> 
[17187049.320000] ata1: command 0xca timeout, stat 0xd0 host stat 0x21
[17187049.320000] ata 1: translated ATA sat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
[17187049.320000] Buffer I/O error on device sda5 logical block 6182
[17187079.320000] ata1: command 0xca timeout, stat 0xd0 host stat 0x21
[17187079.320000] ata 1: translated ATA sat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00[17187049.320000] [17187079.320000] Buffer I/O error on device sda5 logical block 23400635
[17187109.320000] ata1: command 0xca timeout, stat 0xd0 host stat 0x21
[17187109.320000] ata 1: translated ATA sat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00[17187049.320000] [17187109.352000] EXT3-fs error (device sda5): ext3_find_entry: reading directory #622806 offset 0

That message then kept on repeating itself using only somewhat different numbers per line, until I shut the system down from the main power button.

The system seemed to start up alright after that, but does anyone have any ideas on what needs to be done now?

This is a Kubuntu Edgy 6.10 system and the HDD was a Maxtor Diamondmax 9 Plus SATA 120GB

---

### Post by Giltine238 on 2007-04-17
I am currently experiencing a similar problem. My HDD is also a Maxtor. Have you tried checking the S.M.A.R.T. data?

---

### Post by Nesnej Trick on 2007-04-17
> **Giltine238 said:**
> I am currently experiencing a similar problem. My HDD is also a Maxtor. Have you tried checking the S.M.A.R.T. data?

Just did, it didn't help diagnostics quite that much as smartctl is unable to start S.M.A.R.T. on the drive:
> jensen@jensen-desktop:~$ sudo smartctl -s on -T verypermissive /dev/sda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

unable to fetch IEC (SMART) mode page [unsupported field in scsi command]


---

### Post by Nesnej Trick on 2007-04-20
It's happened a few times more while I've been playing Enemy Territory. I've also noticed that prior to the crash, the Maxtor drive makes a clicking noise as if it was parking a drive head during shutdown. This problem seems to occur mostly in 3D applications. For what reason, I don't understand. The general pattern seems to be that the program works fine as long as you're using only data that's cached in the RAM. The system hard freezes as soon as you do something out of the ordinary and have to access the HDDs for any additional information.

Why these crashes occur, I don't know, especially since both programs have only small configuration files on the Maxtor HDD (my /home partition), with the bulk of all needed files laying on my older Western Digital HDD, which has worked flawlessly so far.

---

### Post by Nesnej Trick on 2007-04-22
I've also noticed that after the drive clicks, I have to shut down the system manually. This meaning that the shutdown procedure leaves the system in a state where nothing is being displayed on the monitor, but the system it still fully powered up and all fans are spinning.

Anyone?

---

### Post by Swab on 2007-04-22
Certainly sounds like the drive is dying.. 

 I've been waiting for one of my drives to die so I can try out SpinRite!  It's a commercial app, but apparently it is fantastic at fixing broken drives.

---

### Post by NullHead on 2007-04-22
I've noticed that in my experience when a hard drive does this it is generally loosing power. I recommend that you all check your cable coming from the power supply box (generally in the top left corner) and see how much devices are hooked up to it. Fans don't work well with hard drives and usually do this sort of thing.

---

### Post by Nesnej Trick on 2007-04-24
I think you found the reason. The drive is hooked up so that the same power cable hosts both hard drives and the Radeon 9800 Pro video card, so it explains why the system stalls only when the video cars is stressed. I wouldn't recommend such a cable configuration even to myself, but unfortunately that was the only way I could hook everything up in this Abit Digidice mini-pc. I guess I'll just have to refrain from gaming until I can get a better power supply (the SFF one that comes with this mini-pc can only feed 250W and has way too short power leads for its own good).

> **NullHead said:**
> I've noticed that in my experience when a hard drive does this it is generally loosing power. I recommend that you all check your cable coming from the power supply box (generally in the top left corner) and see how much devices are hooked up to it. Fans don't work well with hard drives and usually do this sort of thing.

---

### Post by pickarooney on 2007-07-17
Just wondering about the outcome of this. I've had a similar problem lately and it turns out (I'm 90% sure) that a crappy nvidia graphics driver in combination with my ATI chipset was causing the problem. This was after I'd replaced the hard drive.

---

