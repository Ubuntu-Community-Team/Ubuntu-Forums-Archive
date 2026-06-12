---
title: "no sound on toshiba a200-12x"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by mokojin on 2007-07-04
hi i

i've complety followed the instrutions on [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and i still don't have any sound.

some info:

Codec: Realtek ALC861-VD
Address: 0
Vendor Id: 0x10ec0862
Subsystem Id: 0x1179010c
Revision Id: 0x100001

and i got these sound modules loaded: (lsmod)

snd_hda_intel         309664  2 
snd_pcm_oss            50176  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                93960  2 snd_hda_intel,snd_pcm_oss
snd_seq_oss            38912  0 
snd_seq_midi_event     10240  1 snd_seq_oss
snd_seq                63392  4 snd_seq_oss,snd_seq_midi_event
snd_timer              27400  2 snd_pcm,snd_seq
snd_seq_device         10900  2 snd_seq_oss,snd_seq

anyone with a similiar problem or solution??

---

### Post by corrosion on 2007-08-10
Sorry but...

How did you make to have wireless working? :confused:

which arch did you install? 64bit or 32bit?

Thanks

---

