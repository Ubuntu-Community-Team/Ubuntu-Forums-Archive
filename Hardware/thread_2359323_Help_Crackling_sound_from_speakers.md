---
title: "Help: Crackling sound from speakers"
date: 2017-04-22
forum: Hardware
---

### Post by hdurr on 2017-04-22
Hi, y'all
I'm pretty new to Linux, and to Ubuntu, so please do pardon me if this is somehow a dumb question, but I have a bit of a problem with sound.

Thing is, the speakers make a rather disturbing crackling sound pretty much all the time. At the same time, the earphones play everything alright.

I've tried surfing the web a bit and it seems my sound card isn't entirely compatible with ALSA, but there seems to be some sort of workaround. Problem is, my system seems different from all the [SOLVED] cases I've seen. I mean there probably is something out there, but I haven't managed to google it out yet.

So can anyone recommend a way to get proper sound again?

Here's the audio info from lspci:
[HTML]00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)[/HTML]

Also, data on driver in use:
[HTML]lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Dell 5 Series/3400 Series Chipset High Definition Audio
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f7d40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
[/HTML]

Does anyone have a good idea what this is all about and what to do about it? The crackling is really disturbing most sound-related activities.

PS If you need more system stats, be sure to let me know :)

---

