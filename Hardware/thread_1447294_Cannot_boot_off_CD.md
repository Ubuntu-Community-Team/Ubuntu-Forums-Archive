---
title: "Cannot boot off CD"
date: 2010-04-05
forum: Hardware
---

### Post by Motorhead Kaze on 2010-04-05
Hi. My trouble is, I cannot seem to get the PC to recognize that there is a disc in the drive at startup. I wanted to reinstall a fresh Ubuntu, but the PC is ignoring the CD and going right to the HD. 

1. BIOS tells me that the CD drive is 1st in line for booting.
2. The CD drive works great for other jobs -- viewing files or burning.
3. I tried booting off older Ubuntu disks and the XP disc, but the PC ignores them all and goes right to the OS that is installed in the HD.
4. I tried booting off the CD from both a totally shut down state, and from a restart as well. No dice.

I am think the issue it is hardware because my setup in BIOS is as I think it should be, but I cannot be sure.

I am running a dual boot Hardy/XP off an Elite Group A770M-A motherboard, with a CD drive, no floppy at all. I have not actually tried REinstalling Ubuntu on this particular PC, though clearly I was able to boot off the disc before because I have 2 working systems on the computer now. The manual mentions nothing about a key to force the CD to boot first.

Do you have anywhere I could start looking to figure this out?

thanks

---

### Post by byStanderone on 2010-04-05
...you could try observing the boot process, taking particular notice on the stage wherein the system is trying to read the cd itself. if it does try to read that track and finds nothing, perhaps it's a hardware problem...assuming that your cd is in good condition.

---

### Post by Motorhead Kaze on 2010-04-05
During the boot process the moment it checks to see if there is a CD in the drive it is so fast that it took me several tries to read that there is no CD found. It is lightning fast, not hanging as if it were attempting to read.

It does this with any startup disc, I tried the Hardy, Jaunty, Karmic and XP OS disks. The drive works for everything else.

---

### Post by byStanderone on 2010-04-05
...you can use the pause/break key to catch the screen, anyway it seems that the boot sequence is ok.

---

### Post by Motorhead Kaze on 2010-04-08
Cool. I will try that and see what happens.

---

### Post by Motorhead Kaze on 2010-04-08
Ok, when detecting drives I get no error messages. Atapi CDROM is listed as the primary drive, then my hard drives are listed.

After this, a very quick JMicron message comes up which reads, "Detect drives done, no any drive found", but I Googled this message and I found:

"Detect drives done, no any drive found&#8221; is a JMicron message. You don't have any PATA drives, you have SATA, so there aren't going to be any drives found."

I am pretty sure that this message has always been there, I just never really paid it much attention.

It isn't an emergency that I reinstall, but the PC is getting slow and it has been a while since I installed Hardy. Might be good to get rid of excess crap I have loaded in here. But that really isn't the issue now, not being able to load off the disk is a BAD thing. Anyone who can offer further useful advice, please speak up.

---

### Post by Motorhead Kaze on 2010-04-13
Bump???

Cannot boot off any OS CD and it is annoying.
I put in an Ubuntu/XP disc, switch on, and the PC ignores the CDRom entirely. The drive works great when logged in, and in BIOS the CDROM is set to fire off first. So...wtf?

EDIT by the way, my current motherboard has no slot for my floppy drive, so installing off the floppy is not gonna happen.

---

### Post by Motorhead Kaze on 2010-04-13
Anyone? Nobody in all of Ubuntu-land can offer help?

---

### Post by rcaca0 on 2010-04-13
I have ran into a similiar situation before and I had to set up the bios to only read from the CD Rom (ie don't allow it to boot from anything else).  Also have you tried to use another CD rom?

---

### Post by byStanderone on 2010-04-15
...maybe i missed something, you haven't said anything booting those bootable disks on another box...if they all bootup or not.

---

### Post by Motorhead Kaze on 2010-04-27
Hello again. Yes, hese are all discs I have used to install versions of Ubuntu on both my desktop (the current problem child) and my laptop. The latest laptop install was with my Karmic disk about 2 months ago.

I was considering unplugging the hard drives so that only the CD would be available, and try to run the live disk that way, but switching them off in BIOS sounds even easier! No screwdrivers required. Let me try that.

---

### Post by Motorhead Kaze on 2010-11-22
Ended up running just the CDRom, then plugging in the hdd after the live disk started up.

---

### Post by wilee-nilee on 2010-11-22
> **Motorhead Kaze said:**
> Ended up running just the CDRom, then plugging in the hdd after the live disk started up.

You might want to know about the per-session boot from menu. It is a key prompt like getting to the bios mine is f12 yours may be different. It is a post bios boot from menu check it out it will probably fix all the problems with booting any cd.

---

### Post by Motorhead Kaze on 2011-07-24
Aaahhh yes, my new motherboard came with that! My old one did not have that option. Anyhow, once I got the new mo.bo. the computer starts from disc as it should (according to the startup order I have listed in BIOS)

So...problem was in the MOBO.

---

