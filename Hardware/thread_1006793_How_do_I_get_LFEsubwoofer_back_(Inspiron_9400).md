---
title: "How do I get LFE/subwoofer back? (Inspiron 9400)"
date: 2008-12-09
forum: Hardware
---

### Post by OttifantSir on 2008-12-09
I'm on Ubuntu 8.10 with these soundcard specs:

```
**cat /proc/asound/card0/codec#* | grep Codec**
Codec: SigmaTel STAC9200
Codec: Conexant ID 2bfa

 **aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -vv (Just the audio part)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Device 01cd
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

I have been annoyed by the subwoofer not "throttling down" when I use the volume buttons (now know how), so in a haste (never a good thing) I added this line to my /etc/modprobe.d/alsa-base file:

```
options snd-hda-intel=ref
```

It didn't do anything except take away my ability to control/use LFE/Subwoofer. It's gone from alsamixer, Gnome-alsamixer and volume control applet.

Anyone know how to get it back without doing a fresh install? (Really like how I got it set up this time)

I have removed the offending code from alsa-base and rebooted. 

I have tried adding **dell-m27** (as per this list: [http://ubuntuforums.org/showthread.php?t=820959]("http://ubuntuforums.org/showthread.php?t=820959") instead of **ref**. 
I have gone through Synaptic and completely removed alsa-base and reinstalled it. (Should I try using --purge with apt-get at CLI?)

Any more info you need, please give me the commands to get it.

Please help! I am just this tin(n)y problem away from having a perfect (for me) setup!

---

### Post by OttifantSir on 2008-12-17
I know people have asked this before, and I have tried quite a few posts, but won't someone please help?

---

