---
title: "Audio problems revisted"
date: 2009-01-31
forum: Hardware
---

### Post by relambert on 2009-01-31
Hello to all, 
First, let me start off by saying that I'm back using Ubuntu after trying four different distros of Linux. The reason behind that is an ongoing problem with the sound on this computer that I cannot get sorted out. My audio device is an onboard Intel chip.  

00:1f.5 Multimedia audio controller: 
Intel Corporation 82801EB/ER 
(ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Elitegroup Computer Systems Unknown device 1878
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at d800 [size=256]
	I/O ports at dc00 [size=64]
	Memory at fb101000 (32-bit, non-prefetchable) [size=512]
	Memory at fb102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

My sound works, but it will quit working for no reason. This computer has two hard drives. One has Windows XP Pro, and the other has Hardy. The sound works just fine in Windows, but this same problem cropped up with ALL distros of Linux. I also have another computer in the house that's running Hardy with Intel onboard audio, but it's chip is ICH4, not ICH5. That computer works like a top. I have tried to configure Pulse audio, add media players, change the default sound card, and so forth. Nothing has helped. Is ANYONE out there having an issue with this audio chip, or is it just his ONE computer?

---

### Post by relambert on 2009-02-06
This issue may be resolved. I have disabled the onboard audio and installed a stand alone sound card. So far, so good, it has not quit. If anyone else may be having this issue, this may be your only out. I loved how Ubuntu just found the sound card and made it work. NO driver install, just worked.

---

