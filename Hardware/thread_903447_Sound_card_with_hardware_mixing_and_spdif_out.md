---
title: "Sound card with hardware mixing and s/pdif out"
date: 2008-08-28
forum: Hardware
---

### Post by Benjamin_Vedder on 2008-08-28
Hi

I have logitech z5500 digital speakers and would like to know if anyone could recommend a good sound card that can handle hardware mixing and has optical s/pdif out.

I have tried my on-board 8 channel intel hd audio, and it worked quite well with the optical output too, but it does not support hardware mixing. I also have tried creative SB x-fi xtreme audio (which is no real x-fi card) with the exact same result as my onboard card. Then i bought an creative x-fi xtreme gamer card, and spent hours and days to get it working. I had to use 64-bit hardy (although i prefer 32-bit) and had to recompile my kernel to make it work with the alsa driver. I could not get the expansion module to work to get optical output at all, but at least it seems to support hardware mixing. (I can run play music through alsa and play games with oss-output and get sound from both at the same time without even enabling pulseaudio, esd, arts..).

I have found Creative SB Audigy SE in a store near by, does it support hardware mixing? Please answer as soon as possible, im so tired of this right now, so if it works i will go buy it right away.

Thanks in advice.

---

### Post by mandarke on 2008-10-28
i got an SB Audigy SE this morning(ca0106 chipset), it doesn't seem to do hardware mixing from what i can see.

i keep getting "pulseaudio[5904]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy" whenever i try to watch a movie in xvid while having teamspeak2 running.

---

