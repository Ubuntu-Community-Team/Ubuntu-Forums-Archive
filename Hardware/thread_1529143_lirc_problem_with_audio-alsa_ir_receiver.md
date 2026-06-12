---
title: "lirc problem with audio-alsa ir receiver"
date: 2010-07-11
forum: Hardware
---

### Post by flexxxv on 2010-07-11
Hello
I just build a simple ir receiver for the audio port. I tested it with audacity. When I try to use it with lircd or irrecord I get always the following output:

```
sudo lircd --driver=audio_alsa -d hw:0,1 -n
lircd-0.8.6[24501]: config file contains no valid remote control definition
lircd-0.8.6[24501]: lircd(audio_alsa) ready, using /var/run/lirc/lircd
lircd-0.8.6[24501]: accepted new client on /var/run/lirc/lircd
lircd-0.8.6[24501]: ALSA function snd_pcm_hw_params_set_format returned error: Invalid argument
lircd-0.8.6[24501]: hw_params_set_format: Success
lircd-0.8.6[24501]: Failed to initialize hardware

``````
sudo irrecord --driver=audio_alsa -d hw:0,1 test.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: ALSA function snd_pcm_hw_params_set_format returned error: Invalid argument
irrecord: hw_params_set_format: Success
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```(no lirc is not running at this point...)

My Sound card:
```
05:03.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
```Kernel:
```
2.6.32-23-generic
```OS
```
ubuntu 10.04 Lucid
```anyone here knows what the problem is? ](*,):frown:

---

### Post by flexxxv on 2010-07-15
*bump*
Sorry I hate to do this, but I still havn't find a solution...

---

### Post by IcarusR on 2010-07-15
How is the receiver connected ?
Does ubuntu see it ?

---

### Post by flexxxv on 2010-07-15
@IcarusR
As I wrote in the first post it is connected to the audio port. So it is the mic in port. I tested it with audacity and it is working all right.
So Ubuntu won't see it as an receiver because I'm just using the sound card, but I should be able to use it with "--driver=audio_alsa".
For more info about the receiver take a look at:
[http://www.lirc.org/ir-audio.html](http://www.lirc.org/ir-audio.html)
I build the same device with another ir module I had laying around. 5V comes from an USB port.
Theoretically I should even be able to execute the command successfully with no receiver connected. So I'm doing something wrong or there is some kind of bug.

Hope someone can help!

---

### Post by IcarusR on 2010-07-15
Sorry got confused. 

> lircd-0.8.6[24501]: ALSA function snd_pcm_hw_params_set_format returned error: Invalid argument

Seems that Alsa does not like 'snd_pcm_hw_params_set_format' where ever that comes from. The lircd alsa driver I guess.

Could post to the lircd mailing list.

Could try downgrading lirc to earlier version & see if that works.

Not very helpful, but can not think of anything better !

---

### Post by flexxxv on 2010-07-23
So I just did an downgrade of lirc. But this won't help at all. but thx for trying to help!

---

### Post by flexxxv on 2010-07-23
So some update:
I tried to use arecord to try accessing the sound card via command line. It is only working by doing something like:
```
arecord --device=hw:0,1 -f S16_LE > test.wav
```
I can only use S16_LE as sampling format. Could this be a problem with irrecord? In case yes: is there any way to tell irrecord to use this sampling format?

---

### Post by cyberwizzard on 2011-08-08
I know this is an old topic but since it took me a while to find the fix for this I'm sharing it here:

The error comes from the fact that LIRC is attempting to open the ALSA input in mono mode where the driver only supports stereo recordings. This is fixed by telling LIRC which channel (left or right) you want to use like this:

```
irrecord --driver=audio_alsa -d hw@48000,r file
```

---

