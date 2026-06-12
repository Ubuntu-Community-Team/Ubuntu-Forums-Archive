---
title: "No HDMI sound in ACER 5930"
date: 2010-01-26
forum: Hardware
---

### Post by lobo99 on 2010-01-26
Hello
I watch the video with HDMI, but no sound.
I have Ubuntu 9.10.
I don't have any digital dive in my sound preferences:
Capture: HDA Intel - ALC888 Analog (PulseAudio Mixer)
Capture: Monitor of HDA Intel - ALC888 Analog (PulseAudio Mixer)
HDA Intel (Alsa mixer)
Playback: HDA Intel - ALC888 Analog (PulseAudio Mixer)
Realtek ALC888 (OSS Mixer)


# aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC888 Analog [ALC888 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0

# lspci 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 013f
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at f6a00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Thanks!

---

### Post by mörgæs on 2010-01-27
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

