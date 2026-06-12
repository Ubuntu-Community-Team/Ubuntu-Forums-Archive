---
title: "No sound in Xubuntu 8.04.1 - Intel integrated sound card"
date: 2009-08-20
forum: Hardware
---

### Post by maximilion on 2009-08-20
I just installed it from the LiveCD, I have everything running except the audio.

No sound neither on front panel jacks nor motherboard green jack. No volume control, and AFAICT there's no "sound control panel" like in Ubuntu 7.10 I installed on another PC.

It's a P4 2.8 GHz desktop from 2005-6 or so with integrated network card and audio. 

I could list that terminal command output thing or the exact hardware specs, but it seems it recognizes it, as I can select "Intel ICH5" - but no controls are recognized/selectable.

So I think I just need a mixer. Which one should I get that "just works"? I need no performance or anything. Should I use Add/remove, Synaptic, or some other method to get it?

Cheers for any advice.

Edit: aplay -l and lspci -v outputs, sorry for the Swedish:

```
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: ICH5 [Intel ICH5], enhet 0: Intel ICH [Intel ICH5]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: ICH5 [Intel ICH5], enhet 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

--------
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7580
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at dc00 [size=256]
	I/O ports at d800 [size=64]
	Memory at febffa00 (32-bit, non-prefetchable) [size=512]
	Memory at febff900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

---

### Post by maximilion on 2009-08-20
Sorry for kinda wasting your time. The reason there was no volume control on the task bar was that the LiveCD hasn't put one there... weird... and me being oh so afraid to mess stuff up.

Became suspicious when I saw I had all the alsa files installed and I tried a .wav in aplay -vv and saw the meter bouncing.

Was all a matter of right-clicking the task bar, add Volume Control, double-click it and make sure the PCM etc sliders were audible.

When I double-clicked an mp3, Totem just downloaded the correct codecs and started playing it. Easy peasy :)

---

