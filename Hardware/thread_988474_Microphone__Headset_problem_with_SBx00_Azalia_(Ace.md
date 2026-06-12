---
title: "Microphone / Headset problem with SBx00 Azalia (Acer Aspire 6530)"
date: 2008-11-20
forum: Hardware
---

### Post by Cold Day on 2008-11-20
Hello people, I am aware that this problem was reported many times in the past, but since I couldn't find any solution, please point me to the right direction if I missed something.

I use 8.10/x86_64 on Acer Aspire 6530, which has

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]

Internal microphone doesn't work and headset/external microphone jacks as well, actually as they don't exist, both in Skype and in all other apps. I tried all options in mixer, all capture combinations etc. -- nothing. Tried to update ALSA to 1.0.18a, no effect.

My only option for now is to but bluetooth headset and try it, but I hope someone found a solution for this annoying problem.

The hardware details:

01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
	Subsystem: Acer Incorporated [ALI] Device 0166
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at cfeec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Acer Incorporated [ALI] Device 0166
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by quip on 2008-12-23
I'm wondering if you were able to solve the problem, or if anyone else has.  I have (I believe) the same audio setup in a Toshiba, and I can't get any kind of microphone working.  It would be nice so that I could use my new laptop for Skype.

---

### Post by quip on 2009-01-07
Just an update:  I tried in vain for a while to get the mic going.  I tried to update alsa by hand compiling, disabling pulse audio, etc....

Nothing worked.  Then, I came across a similar post that stated a switch to OSS (which I guess is currently being developed, which I didn't know) would solve the problem.  It did.  I think the sound output is of slightly less quality than alsa, and I have to restart it (sudo soundoff/sudo soundon) each time I come out of a suspend/resume cycle, but the performance is more than tolerable and the mic now works.

For someone who is not concerned with an advanced sound output setup, I would advise a switch to OSS following the following wiki, which I did.

[https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")

---

### Post by uiteoi on 2009-02-09
I have the same problem, please help.

Computer is Toshiba Satellite  U405D-S2902.
# lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
# uname -a
Linux Thermalgy-Ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

No sound input tested w/ sound recorder and skype. Sound output works fine. Already tried replacing pulseaudio with esound, still not working. I need decent quality audio, mostly for Skype.

Thanks in advance.

---

### Post by williamson389 on 2009-02-11
I have the same problem, any help would be appreciated.

---

### Post by simon.hanna on 2009-11-16
I know this post is old.. but i had this problem on my acer aspire 6530G and solved it by opening alsamixer and found out that the volume of my mic was down, so i pulled it up and then under capture i choosed "int mic" under "Input so"
that did it for me... i didn't have to change anything else... i am still a linux-newbie, so i just played around a little.... ;-)

---

### Post by Necrocide on 2010-01-01
got this working for me also under 9.10 had to uninstall pulseaudio. Check out this post.[http://n2.nabble.com/Re-Ubuntu-s-switch-to-pulseaudio-broke-accessibility-for-the-blind-td3886061.html]("http://n2.nabble.com/Re-Ubuntu-s-switch-to-pulseaudio-broke-accessibility-for-the-blind-td3886061.html")

---

### Post by sarmadzhiev on 2010-05-18
This bug seems to be plague all hda SBx00 microphones
I saw a bug 480815 and the user gilianphilippo had a working solution. I have tweak it a little and tested it works on NV53

Add following 
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
to /etc/modprobe.d/alsa-base.conf 
and restart

---

