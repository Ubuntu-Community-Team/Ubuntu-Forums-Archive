---
title: "[SOLVED] No sound (possibly to do with Songbird?)"
date: 2008-08-03
forum: General Help
---

### Post by japtar10101 on 2008-08-03
I have no sound on my system.  I've tried to follow the guide here:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=VT82xx+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=VT82xx+sound)
But so far, no luck.  My alsamixer is jacked way up, and I still get nothing.

The problem may partly have to do with Songbird, which I installed manually and has, at times, made the audio stop working.  However, usually the problem was amended by rebooting.

Since the problem is quite permanent, it may be likely that a recent update has caused my sound card to malfunction.  I've checked with Rythmbox, and that didn't play any audio either.

In any case, here's the stats I get about my sound card:
```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
~$ sudo lspci -v
.....lots of info, but the most relevant:.......

04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at ff3fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0
```
```
~$ /usr/sbin/Songbird/songbird
doEULA
doFirstRun
doMainwinStart
SBAppInitialize
SBVideoInitialize
setting outerWebPlaylistShowing to: false
setting outerWebPlaylistShowing to: false
setting outerWebPlaylistShowing to: false
setting outerWebPlaylistShowing to: false
SBInitialize *** 
setting outerWebPlaylistShowing to: false
setting outerWebPlaylistShowing to: false
setting outerWebPlaylistShowing to: false
setting outerWebPlaylistShowing to: false
setting outerWebPlaylistShowing to: false
setting outerWebPlaylistShowing to: false
setting outerWebPlaylistShowing to: false
setting outerWebPlaylistShowing to: false
OverlayLoader.loadOverlayList()
	+chrome://shoutcast-radio/content/playlist.xul
OverlayLoader.loadPlayerOverlays() loading overlay chrome://shoutcast-radio/content/playlist.xul
OverlayLoader.loadPlayerOverlays() finished loading overlays
setting outerWebPlaylistShowing to: false
setting outerWebPlaylistShowing to: false
```

Thanks in advance!

---

### Post by japtar10101 on 2008-08-10
6 days, and no response....:(

---

### Post by SunnyRabbiera on 2008-08-10
Well it depends on the nature of the issue, plus this place gets filled up with questions real fast.

---

### Post by cariboo on 2008-08-10
Have you tried in a terminal:

```
sudo /sbin/alsa reload
```

Just to see that the proper modules are loaded.
I had no sound other day after changing the sound card in command line only installation. By running alsa reload and then alsamixer things work just like they should have. The origional sound card was the same chipset as your's, but I didn't like the sound quailty, and I found a Diamond AU88X2 based sound card in a box of miscellaneous pci cards I had shoved in the corner of my shop.

Jim

---

### Post by japtar10101 on 2008-08-22
> **cariboo907 said:**
> Have you tried in a terminal:

```
sudo /sbin/alsa reload
```

Just to see that the proper modules are loaded.
I had no sound other day after changing the sound card in command line only installation. By running alsa reload and then alsamixer things work just like they should have. The origional sound card was the same chipset as your's, but I didn't like the sound quailty, and I found a Diamond AU88X2 based sound card in a box of miscellaneous pci cards I had shoved in the corner of my shop.

Jim
No luck so far...
```
omiyat@OMIYATPC:~$ sudo /sbin/alsa reload

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/omiyat/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 6112(pulseaudio) 6318(mixer_applet2). 
Unloading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-mpu401-uart snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device (failed: modules still loaded: snd-hda-intel snd-pcm snd-page-alloc snd-hwdep snd-timer).
Loading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-mpu401-uart snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

```

---

### Post by japtar10101 on 2008-08-24
I'm an idiot: It's the speakers, not the OS.

---

