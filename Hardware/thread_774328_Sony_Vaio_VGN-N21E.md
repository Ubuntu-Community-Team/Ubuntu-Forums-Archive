---
title: "Sony Vaio VGN-N21E"
date: 2008-04-29
forum: Hardware
---

### Post by phoof on 2008-04-29
Hello all, I'm trying to get my audio working properly on my laptop under Ubuntu 7.10. When I plug in my headphones the audio still plays through the speakers. If you need more info let me know.

lsmod | grep snd output:

```

snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

```

And grep Codec /proc/asound/card0/codec#* output:

```

/proc/asound/card0/codec#0:Codec: Realtek ALC262
/proc/asound/card0/codec#1:Codec: Conexant ID 2c06

```

Thanks for any help in advance.

---

