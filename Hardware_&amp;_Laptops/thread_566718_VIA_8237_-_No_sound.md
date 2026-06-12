---
title: "VIA 8237 - No sound"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by mikkyb on 2007-10-03
I am unable to produce any sound from my system on Ubuntu (Kubuntu) feisty. I've read and tried so many things to fix this problem:

[LIST]
[*]Download compiled and installed ALSA drivers
[*]Configured ALSA drivers
[*]Unmuted relevant AND seemingly unrelated channels (all combinations you can imagine!)
[*]Tested my speakers on another system - they work fine
[*]Tested in Windows XP - sound works
[/LIST]

But to no avail, I scoured the web for hours and hours... lots of people seem to have the same problem, and are consistently offered the same (above) solutions.

I was once getting REALLY quiet sound from 1 speaker (2.1 setup) but you had to put your ear up to the speaker to hear it though - with the volume on the amplifier and mixer all the way up.

It's quite frustrating. But if anyone has anything else to try I'm certainly willing. I'm thinking I'll probably just buy a new sound card tomorrow though - I figured I'd go with a Sound Blaster Audigy or something? It should be well supported yeah?

But if someone wants to help me save a few bucks I'd certainly be appreciative.

[edit:] Forgot to post a bit of info:
```

**lspci | grep audio**
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

**cat /proc/asound/version**
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).

**cat /proc/asound/cards**
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with VIA1617A at 0xdc00, irq 19

**cat /proc/asound/cards**
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with VIA1617A at 0xdc00, irq 19

**cat /proc/asound/devices**
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 1]: digital audio capture
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture

**cat /proc/asound/timers**
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-0-2: PCM playback 0-0-2 : SLAVE
P0-0-4: PCM playback 0-0-4 : SLAVE
P0-0-6: PCM playback 0-0-6 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-1-1: PCM capture 0-1-1 : SLAVE

**cat /proc/asound/pcm**
00-01: VIA 8237 : VIA 8237 : playback 1 : capture 1
00-00: VIA 8237 : VIA 8237 : playback 4 : capture 1

**lsmod | grep snd**
snd_via82xx            29208  4
snd_ac97_codec         98464  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  5 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9472  1 snd_via82xx
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
gameport               16520  2 snd_via82xx,analog
snd                    54020  17 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
```

Cheers,
Mike.

---

### Post by komasoftware on 2007-11-06
mikkyb,

Any progress on this ?
I got the exact same prob. Actually after installing gutsy the sound was working fine at first, but very low. I read in the forums that one should disable the flag 'External Amplifier'. After opening the alsamixer I never got any sound back again.
In my previous setup - Feisty - sound was troublesome too. It used to work - but on a very low level too - and then suddenly quit with a sudden 'crack' in the speakers.

Still hoping to find a solution for this .... and finish my mythTV ;-)

Koen

---

