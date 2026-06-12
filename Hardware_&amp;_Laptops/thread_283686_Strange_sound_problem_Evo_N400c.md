---
title: "Strange sound problem Evo N400c"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by trbloomer on 2006-10-24
Ok, this is a small problem but it makes me a little nuts. After searching and fining others with a similar problem but no solution I thought I'd ask.

In both Edgy and previously in Dapper, the sound in my laptop works but only after I adjust the sound up or down with the hardware buttons on the machine. Its a weird problem. I assume its some sort of initialization thing.

Here is the result of lsmod | grep s
snd_maestro3           27524  1 
snd_ac97_codec         97696  1 snd_maestro3
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_pcm                84612  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    58372  12 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd

and for  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCI [ESS Allegro PCI], device 0: Allegro [Allegro]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

Anyone have any ideas?

Thanks

---

### Post by RobbMeex on 2008-01-20
Not too strange, cause mine does it too.

---

