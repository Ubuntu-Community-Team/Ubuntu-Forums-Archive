---
title: "No sound in 8.10 after update"
date: 2008-11-08
forum: Hardware
---

### Post by Spartacus84 on 2008-11-08
After a recent update, the sound on my Compaq Presario f756nr has stopped working. Whenever a sound would play, it plays a weird scratching, clicking noise instead. I thought it might mean something was broken on my laptop, but I tested the sound on a live cd and it works fine. What could be the problem?

---

### Post by Spartacus84 on 2008-11-08
Also, this is what it says in lspci -v.

```
Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

EDIT: And when I run it as root:

```
Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Device 30ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 
Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

---

### Post by purduepilot on 2008-11-08
I had the same problem a couple days ago.  Burned 8.10 to a cd and formatted my / partition and did a clean install of 8.10.  Sound works fine now, but now I can't mount my external hard drive.

---

### Post by Ecologger on 2008-11-08
Sometimes when the PCM volume is all the way down it makes those poping sounds. Check that, sometimes you might have to cycle through your devices in the alsa mixer to get it to work.

---

### Post by Spartacus84 on 2008-11-08
> **Ecologger said:**
> Sometimes when the PCM volume is all the way down it makes those poping sounds. Check that, sometimes you might have to cycle through your devices in the alsa mixer to get it to work.

Ah, yes, that was it. Just had to turn up the PCM volume. Thank you.

---

### Post by Ecologger on 2008-11-08
NP. Mark it as solved.

---

