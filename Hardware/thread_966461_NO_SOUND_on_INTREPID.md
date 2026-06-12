---
title: "NO SOUND on INTREPID"
date: 2008-11-01
forum: Hardware
---

### Post by fahdovski on 2008-11-01
i Have no sound on Ubuntu INtrepid plz Help me

i have this 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD 

codec alc883 and alc268

---

### Post by fahdovski on 2008-11-01
HELP pLZ

---

### Post by everthonvaladao on 2008-11-01
===> here's a quick FIX: [[How to quickfix the "no sound" issue in Ubuntu Intrepid 8.10]]("http://mobilevs.blogspot.com/2008/11/how-to-quick-fix-no-sound-issue-in.html")

;-)

P.S.: PulseAudio sucks!

---

### Post by fahdovski on 2008-11-01
i installed OSS its works

---

### Post by Skerit on 2008-11-03
When are they *really* going to fix this?

At first I couldn't believe pulseaudio made it into 8.04, now I can't believe it's still as unstable as it was then! 

I also do not understand why they're bickering over Openoffice 3.0, why they chose NOT to ship it,  when they're hapilly using this faulty audio subsystem.

---

### Post by jbmurphy on 2008-11-03
In 8.04 Had no sound issues. Same machine upgrade to 8.10 with this sound chip:

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 0253
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 255
	Region 0: I/O ports at 1000 [disabled] [size=256]
	Region 1: I/O ports at 1400 [disabled] [size=64]
	Region 2: Memory at 90000400 (32-bit, non-prefetchable) [disabled] [size=512]
	Region 3: Memory at 90000600 (32-bit, non-prefetchable) [disabled] [size=256]
	Capabilities: <access denied>

But get no sound card detected. Have tried all the quick and some long fixes still no joy.

--john


downloaded latest source from alsa project. Built with --with-cards=intel8x0 arg to configure

---

### Post by BLTicklemonster on 2009-02-28
I just went to system, preferences, sound and set all my stuff from auto to my sound blaster, and I'm listening fine. Surround works with no fidgeting for the first time now, too. 

HEY UBUNTU DUDES, DROP PULSE AUDIO FROM DEFAULT INSTALL, AND LET THOSE WHO GIVE A FLYING RAT'S PATOOTIE INSTALL IT AFTER THEY'RE UP AND RUNNING, OKAY?

---

