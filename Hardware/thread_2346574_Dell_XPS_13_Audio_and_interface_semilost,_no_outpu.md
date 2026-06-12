---
title: "Dell XPS 13 Audio and interface semilost, no output on jack  ubuntu 16.04"
date: 2016-12-16
forum: Hardware
---

### Post by jacopo.tolja on 2016-12-16
The system is an -XPS-13-9350 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

The main problem was that there was no audio output at the jack for the headphones
If the jack was inserted the audio stopped but no signal was coming  out

I made an audio test and I change the surround option and since the device listed in the Audio Setting disappeared and the volume audio icon in the top bar is greyed.
All sounds where gone but the drum on startup. After login nothing worked 
After a recent update I got the audio back to work at a fixed volume, but the interface does not permit me to change the volume neither to silence the audio! Icon still greyed

[ATTACH=CONFIG]272730[/ATTACH][ATTACH=CONFIG]272731[/ATTACH]

How do I put back this device in the sound setting?

```
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21) (prog-if 80)
    Subsystem: Dell Sunrise Point-LP HD Audio
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 283
    Region 0: Memory at dc328000 (64-bit, non-prefetchable) [size=16K]
    Region 4: Memory at dc300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee00338  Data: 0000
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl

aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=PCH
    HDA Intel PCH, ALC3246 Analog
    Default Audio Device
sysdefault:CARD=PCH
    HDA Intel PCH, ALC3246 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC3246 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC3246 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC3246 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC3246 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC3246 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC3246 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
hdmi:CARD=PCH,DEV=2
    HDA Intel PCH, HDMI 2
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC3246 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dmix:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC3246 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC3246 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC3246 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Hardware device with all software conversions
surround21:CARD=PCH,DEV=0
    HDA Intel PCH, ALC3246 Analog
    2.1 Surround output to Front and Subwoofer speakers (OEM backport)
```

---

### Post by Yellow Pasque on 2016-12-17
Start here:
```
rm -r ~/.config/pulse*; pulseaudio -k
```

[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by vanadium on 2017-03-12
Before attempting the above, first try whether this command already solves it:
```

alsactl restore

```
(run the command as regular user)

---

### Post by jacopo.tolja on 2017-04-06
alsactl: state_lock:125: file /var/lib/alsa/asound.state lock error: File exists
alsactl: load_state:1683: Cannot open /var/lib/alsa/asound.state for reading: File exists
Found hardware: "HDA-Intel" "Realtek ALC3246" "HDA:10ec0256,10280704,00100002 HDA:80862809,80860101,00100000" "0x1028" "0x0704"
Hardware is initialized using a generic method


I give up for long time but the problem persist, no audio from the audiojack and the mic disappear and I cannot use skype hangout now the problem is really give me problem!! I need it
Thank you for your help

---

### Post by jacopo.tolja on 2017-04-06
I did it  in terminal nothing happen.

---

