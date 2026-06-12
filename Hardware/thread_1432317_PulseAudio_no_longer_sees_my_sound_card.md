---
title: "PulseAudio no longer sees my sound card"
date: 2010-03-17
forum: Hardware
---

### Post by radu.c on 2010-03-17
Today I lost my sound. I blame it on a possible recent upgrade, but not sure which. ALSA sees my sound card just fine, but Ubuntu says there's no hardware in "Sound Preferences". What gives? It worked until a few days ago.

I'm running Ubuntu 9.10 on a Asus X59GL laptop (nVidia chipset and sound card).

I booted into Windows, and my sound card isn't fried, 'cause it works there. I tried booting earlier kernels, but that didn't fix my sound. I'll be updating this post as I try stuff out.

Downgraded the PulseAudio packages, but no dice.

Booted Ubuntu 9.10 Live CD, sound works just fine.

Reinstalled pulse-audio packages (with purge on remove), removed ~/.pulse*, still broken.

FOUND: timidity was taking over the sound card. I ran pulseaudio -vvvvv and it was like "cards found: 1" and "is busy: yes", so I ran "fuser /dev/snd/controlC0" and nailed the bitch.

Thanks for your help :P

---

