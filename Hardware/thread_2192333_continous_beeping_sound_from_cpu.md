---
title: "continous beeping sound from cpu"
date: 2013-12-07
forum: Hardware
---

### Post by jakelong00 on 2013-12-07
Whenever i was turning on my pc in the last week my cpu was making a constant sound like a "sound of something spinning followed by a small beep" and it didnt use to boot and gave me a read error. now surprisingly it booted today but i am still getting that combination of sound. i dont know whether its the processor or motherboard or harddisk or something else that is making this sound. can someone help me with this? i am on ubuntu 13.10 and now my systems not working properly and is very slow

---

### Post by jon-edwards-i on 2013-12-07
What exactly is the read error message you are getting?

What computer make and model is it?  Desktop or laptop?

When you get the problem is anything appearing on screen or does it stay black?

Can you go into bios and check the hardware monitoring section of it (if present).  Are the temperatures OK and are all fans operational?

If it's not possible to boot using the hard disk, does it boot off a USB stick or CD ROM?

There's any number of things it could be but it really needs to be narrowed down.  For example a failing fan on the processor can cause major slow downs as the CPU will overheat, and then 'throttle' itself resulting in very slow performance.  But that shouldn't cause read errors which would indicate something up with a disk.  Unusual "beeps" on startup can be caused by miscellaneous hardware errors or incorrect bios settings. Sometimes the beeps are in the form of a code (certain number of beeps for bad memory, processor error etc.) but it would only be possible to decipher them if you have the manual for the motherboard.  Also did this start happening suddenly or has it been a gradual decline in performance?

---

### Post by jakelong00 on 2013-12-07
There was nothing else on bootup, just the gigabyte standard logo prompting options for entering into bootup and after 3-4 minutes a black screen with "read error" written.

Its a desktop with gigabyte z77m motherboard,intel i3,ubuntu 13.10 and windows 8 dual boot.

i checked the bios and everything looked fine.

i haven't tried booting off usb or dvd because today when i was going to.. it suprisingly booted normally and haven't shut down my pc yet(taking backup).

the unusual beeps are not caused by the post test done by mobo.( i can hear that short single beep as soon as i power on my pc). i can hear the beeps even when i am working on my pc.

how can i check my cpus temperature?? where in bios??

---

### Post by tgalati4 on 2013-12-07
Look for a tab that says "PC Health".  Otherwise, open up the machine and clean it and verify that the CPU fan is spinning freely.

---

### Post by jon-edwards-i on 2013-12-08
I don't know what the beeping would be if it's something different and distinct from the POST beep.  Is it definitely an electronic beep or could it have a mechanical source?  What you describe about it staying on the logo screen for a long time before failing to boot, I have seen on a PC I've had that had a HDD fault.  But it's not a specific indication of that being the problem, just something I've seen in the past.  The BIOS was struggling to initialise the faulty drive.

Are you comfortable with working inside the PC?  This will easily allow you to see if fans are working OK first of all.  It may also help you pinpoint where the noise is coming from.  If you suspect it might be the HDD at fault, you can disconnect the power and SATA cable from the drive, and try to see if it goes through the POST screens with it disconnected.

---

