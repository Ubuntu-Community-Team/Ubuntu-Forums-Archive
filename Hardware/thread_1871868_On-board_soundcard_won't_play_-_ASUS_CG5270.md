---
title: "On-board soundcard won't play - ASUS CG5270"
date: 2011-10-29
forum: Hardware
---

### Post by seangllghr on 2011-10-29
I've been using Ubuntu on and off for the last six years or so, and used to have a notebook with an uncooperative wireless card, so hardware issues after a fresh install are nothing new to me. I'm baffled by this one however.

I've installed 11.10 on a brand-new hard drive after the last drive (probably) failed. I might be having some issues with the motherboard, but almost everything is working right now, so I'm pressing forward. However, Ubuntu doesn't seem to want to recognize my on-board sound card. The computer has 2 audio controllers, one on the NVidia graphics card for audio output via HDMI, and the other on the motherboard for audio the rest of the time. 

Since I'm using DVi to connect to my monitor (no HDMI port, otherwise the issue would be moot), I'm looking for the audio to output to the on-board card, rather than the HDMI output. The GUI for sound settings doesn't even register the on-board controller, likewise in the console with 'aplay -l'. 'lspci' returns this, however:

> 00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
    Subsystem: ASUSTeK Computer Inc. Device 837b
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fcff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intelfor the on-board controller, which indicates that the system at least sees that it's there. Would this be a driver issue? I've never had problems with it before, and this is my third or fourth fresh Ubuntu install on this machine - though the first with the new drive.

Thanks for the help.

---

### Post by seangllghr on 2011-10-29
Well, never mind. Solved it myself. Turns out it was a driver issue. I needed to tell it to load either 'snd-hda-intel' or 'snd-hda-codec-realtek' during boot.

---

