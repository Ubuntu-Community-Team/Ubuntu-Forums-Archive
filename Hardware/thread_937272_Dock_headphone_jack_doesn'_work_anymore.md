---
title: "Dock headphone jack doesn' work anymore"
date: 2008-10-03
forum: Hardware
---

### Post by mjparme on 2008-10-03
I installed Ubuntu yesterday and everything was great as far as sound goes. My dock headphone jack at first didn't work but then I found a thread here about the IEC958 switch and checking that fixed it.

However, I came in this morning, booted up and the dock headphone jack doesn't work anymore. The updater did install 2 updates this morning but I don't remember what they were so I am unsure if they were sound related.

I have scoured these forums for possible solutions and have tried various ideas (no matter how crazy), this one specifically:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

The strangest thing is that the startup sound that plays at the Ubuntu login prompt comes through the dock headphone jack, but nothing else will! The sound plays but comes through the laptop speakers.

No matter what sound option I choose for the snd-hda-intel model (per the thread I linked above) the behavior is the same (startup sound through the dock headphone jack then all other sound through the laptop speakers).

I have exhausted my troubleshooting ideas. Could anyone provide additional insight? I find it odd that it worked just fine yesterday, but no longer works (and as far as I can tell I made no changes except the 2 updates that installed)

lspci -v
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

```

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

cat /proc/asound/card0/codec#* | grep Codec
```

Codec: SigmaTel STAC9200
Codec: Conexant ID 2bfa

```

---

### Post by mjparme on 2008-10-03
I should also mention that I have confirmed via alsamixer that all the channels are un-muted and that the IEC958 switch is still selected.

The models I have tried for the snd-hda-intel are:

dell-m22 (I have a dell latitude D620)
auto
3stack

The behavior is the same.

I also tried unistalling (with purge) all the sound related packages and reinstalling per this Sticky thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

