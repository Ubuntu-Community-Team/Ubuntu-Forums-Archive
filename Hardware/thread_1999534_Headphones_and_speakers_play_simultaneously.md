---
title: "Headphones and speakers play simultaneously"
date: 2012-06-08
forum: Hardware
---

### Post by barjaktar on 2012-06-08
Hello.

I updated my 10.04 kernel from 2.6.32-38 to 2.6.32-41 and now, when I plug my headphones, the sound goes on both the speakers and headphones. 

I tried installing the new driver, but synaptic says there is none for 41. I tried changing alsa-base.conf in the following way. It used to be:

options snd-hda-intel model=ideapad

and i tried models:

auto; auto-conf; basic; toshiba;

When I go to System - Preferences - Sound I only have one option in Hardware tab: Internal Audio 1 Output Analog Stereo Output.

I use Toshiba Satellite C655.

Here is what lspci says about my audio device:

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d6400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


Everything works fine when I boot into 38 kernel version.

How to make it recognize when I plug in headphones and starts playing just through them in kernel version 41?

Thank you.

---

