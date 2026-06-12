---
title: "Sound problem, help troubleshoot"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by a0peter on 2007-11-14
Hi
I am the proud owner of a Toshiba Satellite Pro U200-128, and i have no sound in Gutsy. I cant remember if I ever had sound using the previous versions.
Whenever I try to adjust the volume it says something along these lines: gnome-volume-control (No such file or directory)

What can I do to fix my problem?

*update*
Here is my lsmod | grep snd:
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_mixer_oss          17664  2 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  9 snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

---

### Post by dabl on 2007-11-14
Probably you want to follow this excellent sound troubleshooting guide:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

:)

---

### Post by a0peter on 2007-11-14
I followed it from a-z but still no sound and the error message from above is still there. It lists drivers and my sound card allrigt, but no sound in any programs. Help?

My card is using the hda-intel driver....

---

