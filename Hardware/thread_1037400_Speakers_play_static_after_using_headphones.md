---
title: "Speakers play static after using headphones"
date: 2009-01-11
forum: Hardware
---

### Post by xinix on 2009-01-11
So I recently installed 8.10 on a new laptop (asus N50) and things seemed to work out of the box just fine.  That is until today.  Sound would play from the speakers like I expected them to.  Today I plugged in headphones and sound stopped coming from the speakers and did come out of the headphones (like it should).  But after unplugging the headphones I only get static noise from the speakers and no sound from the headphones if I plug them back in.

I've tried rebooting and no luck.  The speakers work in Windows and the expressgate os (another minimal linux).

Any suggestions?

Thanks

---

### Post by xinix on 2009-01-12
shameless bump,  what logs would be useful to diagnose this issue?
Did I mention the static plays in stereo?  Also it seems to work with skype for some reason but other things still just give static.

---

### Post by johnnydopefish on 2009-10-06
Bumping this.  I have the exact same problem on different hardware.

Here's my hardware in question: (lspci -vvv)

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 02bc
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at f4800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

I tried to rmmod and modprobe the snd-hda-intel module (for what good it might do) but got errors about it being in use.

I'm using a Dell Vostro 1520, and apparently I'm not the only person who's had [strange sound issues]("http://ubuntuforums.org/showpost.php?p=7887536&postcount=4").

Any other ideas?

---

### Post by johnnydopefish on 2009-10-07
Alright, another diagnostic update.

From System > Preferences > Sound, my defaults were all set to Autodetect.

If I change anything to any of the OSS options, I get a "could not open audio device for playback.  Device is being used by another application" error.  Though some people have reported success with the OSS options for resolving this problem, I am not one of them unfortunately.

If I change anything to ALSA or PulseAudio, that's when I get the horrible static sound.

It appears there is an [open bug report]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/367544") for this issue.

---

### Post by ioggstream on 2009-10-13
this should solve.
Peace, 
R.

[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

---

### Post by johnnydopefish on 2009-10-14
That did solve my problem.  Thank you very much!

---

