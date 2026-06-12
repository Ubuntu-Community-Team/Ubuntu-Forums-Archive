---
title: "[SOLVED] No more sound"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by vertex_vr4 on 2007-11-20
Hi all,

Long time reader first time poster etc etc....
I have a Dell D600 laptop which was working a treat with the new 7.10 release (thanks guys!)
Anyway, the sound was working correctly until last week...then it stopped.

Could anyone help me figure out the problem?

I have tested the following:
1. Its _not_  muted and the sound is "high"
2. I am not deaf :)
3. The correct modules are loaded and "seen" by the sound applet in System->Preferences
4. A music application appears to believe it is playing correctly
5. I turned everything on alsamixer
6. `Dmesg` and syslog/debug  is free of anything related

I will try dropping my HDD into another D600 but other than that I'm out of ideas.....

Cheers,
John

See attached "sndstat"

All the modules appear to be loaded correctly:
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

---

### Post by vertex_vr4 on 2007-11-20
Ok so I lied,

In alsamixer I didn't turn on "external".

If this is your problem do the following:

1. Open a terminal
2. Type "alsamixer"
3. Scoot all the way to the right by using the cursor keys
4. When you land on the item "external" press the keyboard button "m" (obviously)
5. Test again

Cheers,
John

---

