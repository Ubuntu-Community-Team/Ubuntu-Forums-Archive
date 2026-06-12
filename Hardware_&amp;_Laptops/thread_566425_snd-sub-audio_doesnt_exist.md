---
title: "snd-sub-audio doesnt exist"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by victorgreen on 2007-10-03
I have a GWC usb external sound card that doesnt just work when you plug it in... When you hit the volume buttons the card, it does control system volume, but there is no output when you plug speakers into the card. 

the various commands to list sound cards do not acknowledge my little usb's existence. 

Im pretty sure I need snd-usb-audio to make this work, but I have no idea how to get it. 

:~$ sudo modprobe snd-usb-audio
FATAL: Module snd_usb_audio not found.

:~$ lsmod | grep snd
snd_hda_intel         262680  4 
snd_pcm_oss            44800  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81156  3 snd_hda_intel,snd_pcm_oss
snd_seq_oss            35456  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54256  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24452  3 snd_pcm,snd_seq
snd_seq_device          9740  2 snd_seq_oss,snd_seq
snd                    56580  14 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm

---

### Post by victorgreen on 2007-10-07
I compiled Alsa 1.0.15rc3 and the usb works now, but I have other sound issues which I have posted about in other places on the forum, this particular problem is solved.

---

