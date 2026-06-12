---
title: "Asus Pro60 Headphone Jack"
date: 2008-04-25
forum: Hardware
---

### Post by neandero on 2008-04-25
Dears,

I have a working sound card through internal laptop speakers, but
there is no sound when plugging a headphone jack in the audio out.

Model: Asus Pro60
Ubuntu: 8.4

```

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1173
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

Thanks,

---

### Post by neandero on 2008-04-25
well,

finally solved:

```

sudo gedit /etc/modprobe.d/alsa-base

add the line:
options snd-hda-intel model=z71v position_fix=1

```

---

