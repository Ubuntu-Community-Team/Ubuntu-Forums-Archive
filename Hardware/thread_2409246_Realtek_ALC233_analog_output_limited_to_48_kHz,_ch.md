---
title: "Realtek ALC233 analog output limited to 48 kHz, chip supports up to 192kHz"
date: 2018-12-30
forum: Hardware
---

### Post by marko7fcb on 2018-12-30
I have an issue with my onboard laptop audio chip, the Realtek ALC233. Namely, in Ubuntu I cannot make use of all the sampling rates that the chip supports. The chip supports up to 24-bit/192kHz analog stereo output, but in Ubuntu I can only get either 44.1 or 48 kHz. In Windows, I can get up to 192kHz without problems.How do I solve this? Is it possible to manually update the audio drivers to potentially fix this?

---

### Post by Yellow Pasque on 2018-12-31
[https://r3dux.org/2013/12/how-to-enable-high-quality-audio-in-linux/](https://r3dux.org/2013/12/how-to-enable-high-quality-audio-in-linux/)

I don't know if I'd make the default sample rate 24/192. I'd probably make it the alternate sample rate (and then make sure nothing is playing sound before trying to play the 24/192 source).

---

### Post by marko7fcb on 2019-01-19
OK, thanks, but unfortunately the link doesn't help. When I try to play a 24/192 or 24/96 file in Audacious (using the ALSA output), I get this error: "ALSA error: snd_pcm_hw_params_set_rate failed: Invalid argument.". If I attempt to play such a file using PulseAudio, I am able to play the file, but it gets resampled to 48kHz (which I've verified by running "cat /proc/asound/card0/pcm0p/sub0/hw_params").

---

