---
title: "Gutsy Aspire 5050 ALC883 fart-sound (I'm not making this up)"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by JT673 on 2007-12-12
I got the sound to work by turning on "Surround", but whenever I play sound, I get a static/fart noise  

aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

lsmod | grep snd:
```

snd_rtctimer            5344  1 
snd_pcm_oss            50560  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_hda_intel         337448  4 
snd_pcm                95624  3 snd_pcm_oss,snd_hda_intel
snd_seq_dummy           5508  0 
snd_seq_oss            37632  0 
snd_seq_midi_event     10240  1 snd_seq_oss
snd_seq                63776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_timer              28040  4 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device         10516  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd                    70696  15 snd_pcm_oss,snd_mixer_oss,snd_hda_intel,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore              11040  1 snd
snd_page_alloc         12688  2 snd_hda_intel,snd_pcm

```

:confused::confused::confused:

---

