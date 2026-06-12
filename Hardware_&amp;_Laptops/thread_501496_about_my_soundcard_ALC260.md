---
title: "about my soundcard ALC260"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by hjbolide on 2007-07-15
First , sorry about my poor english
   i bought a compaq b1925tu , the sound card is ATI Technologies Realtek ALC260   and it's also marked in the hardware information "SB450 HDA Audio"
   i've tried so many solutions but no one can solve my problem , my computer can detect my sound card but no sound , could anyone help me ?
   great thanks!

$ uname -a
Linux laptop 2.6.22-8-386 #1 Thu Jul 12 15:31:33 GMT 2007 i686 GNU/Linux
$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).
$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0500000 irq 18
$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC260
hjbolide@laptop:~$ lsmod | grep snd
snd_hda_intel         255392  1 
snd_pcm_oss            43264  0 
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                77320  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           3844  0 
snd_seq_oss            31872  0 
snd_seq_midi            8704  0 
snd_rawmidi            24832  1 snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                50416  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22916  2 snd_pcm,snd_seq
snd_seq_device          8332  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    52356  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc          9992  2 snd_hda_intel,snd_pcm

what's the problem?

---

### Post by ugm6hr on 2007-07-21
Have you tried headphones?  If they work - you just need to edit settings in ```
alsamixer
```
Maximise (with up-arrow) volume in PCM and Surround (and unmute with "M").

---

### Post by ugm6hr on 2007-07-27
Perhaps post the output from the command:
```
amixer
```
This will list all the amixer outputs - it is likely that something needs to be unmuted or turned on.  Worth trying the suggestion in my previous post in any case, even if headphones don't work.

---

