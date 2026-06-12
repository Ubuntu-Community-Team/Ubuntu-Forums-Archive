---
title: "Excessive CPU usage and lockups after installing old SoundBlaster Live on Edgy"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by Grady Lemoine on 2006-12-30
Hi all,

I just installed an old SoundBlaster Live! card I had laying around in an attempt to get slightly better sound out of my system.  I had no trouble installing it; the system silently recognized the card and used it for sound output.  However, not long after I installed it, I noticed that CPU usage was pegged at 100% (on both cores of my dual-core machine) and CPU clock speed was up at maximum.  Shortly thereafter, my computer stopped responding.  I removed the new card, but the problem continued: I get a few seconds to a few minutes from when I log in to when the system locks, and CPU usage is 100% (mainly allocated to the "nice" usage type if I recall the System Monitor correctly).  CPU temperature was getting high (up to about 45-47 deg C), but I don't think that's high enough for a hardware lockup.  I have gotten some very sluggish response after I thought the system was completely locked up, so it may be that whatever-it-is is just starving everything else of CPU time.  The system runs fine when I boot from the install CD, so it's clearly a software issue.

The relevant parts of my system are as follows:

ASUS A8N VM CSM motherboard (uses nvidia 430 southbridge and 6650 northbridge, IIRC)
AMD Athlon 64 X2 3800+ processor (socket 939)
Ubuntu Edgy, with nvidia binary display driver

I think I have the manual any more for the sound card I tried to install, but it says "Model: SB0100" on the board itself, and the largest chip on the board has "Creative EMU10K1-SFF" written on it.  It's about a 2001-2002 vintage board.

I presume from my symptoms that there's something still floating around my system from the sound card, but I don't know how to figure out what.  If it's relevant, when I was looking around in the Device Manager, I also activated a hardware information reporting system (I forget what it was called, but it was a button at the bottom of the right-hand pane, and was supposed to collect up information on my hardware in a non-personal-information-disclosing manner and send it to the Ubuntu developers).  Unfortunately, I didn't think to try to take a snapshot of what kernel modules I was using, etc., before I installed the new card.  Can anyone give advice on how to figure out what the problem is?

Thank you,

--Grady Lemoine

---

### Post by Grady Lemoine on 2006-12-30
Thought I'd tell the forum for posterity -- I fixed my problem.  It turned out not to be anything to do with the sound card, apparently.  For some reason BOINC had decided to go from "not working" to "working too well" and was eating all my CPU cycles; I discovered this by using the good ol' "top" command.  (For some reason, the GNOME System Monitor didn't show this.)  I have no clue why this happened; I didn't install any sofware updates, so I wouldn't have expected any change in BOINC.  Anyway, I used Synaptic to remove it forcibly from my system.  I've installed my sound card again, and everything seems to be working fine, with normal CPU usage.

--Grady

---

