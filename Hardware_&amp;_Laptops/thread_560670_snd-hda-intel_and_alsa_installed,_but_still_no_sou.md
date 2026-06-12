---
title: "snd-hda-intel and alsa installed, but still no sound"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by Jeanpaul145 on 2007-09-26
I have Gutsy beta installed, and out of the box Gutsy recognises my audio card correctly (a Realtek ALC268) and alsamixer is even unmuted, however I still get no sound whatsoever.

However, when the master volume is at max. (100%) then de gain is still 0db (the 4th line of alsamixer states 

" Item: Master [dB gain=0.00, 0.00]   ".) 

Maybe this has something to do with it?

---

### Post by ThrobbingBrain66 on 2007-09-26
```
gksudo gedit /etc/modprobe.d/alsa-base
```
at the end of the file, add this line:
options snd-hda-intel model=auto

Then reboot and you should have sound.  If 'auto' doesn't work, try replacing it with '3stack'

---

### Post by Jeanpaul145 on 2007-09-26
I tried that, but it is as if nothing's changed: still no sound.

I took the time to see if the audio module was even being loaded, and it is:
```

j@znote:~$ lsmod|grep snd
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
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

```

Any ideas?
Dunno if it's important, but I'm using the Gutsy beta, Feisty or earlier is no option sincw I need the new wifi stck to get that functionality working, and I doubt dat sound would work on those since I'm packing the latest Santa Rosa hardware.

---

### Post by Jeanpaul145 on 2007-09-28
bump...

---

### Post by dumshi on 2007-09-28
do u dual boot ? with XP or VISTA perhaps ?

Check to see if the Audio is Muted in XP / VISTA. (Use the Hardware Dial to un-mute).

This is just a crazy idea .. because i happen to run into similar thing few day's back.. 

[http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved](http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved)

If everything else failed, i don't think it's harm trying this :D

Cheers.

---

### Post by brokentire on 2007-09-29
I have a similar problem with my HP dv9548us but I notice the my mute light is lit on my notebook and I don't know how to turn it off....even the remote wont turn it off.

---

### Post by Jeanpaul145 on 2007-10-09
> **dumshi said:**
> do u dual boot ? with XP or VISTA perhaps ?

Check to see if the Audio is Muted in XP / VISTA. (Use the Hardware Dial to un-mute).

This is just a crazy idea .. because i happen to run into similar thing few day's back.. 

[http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved](http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved)

If everything else failed, i don't think it's harm trying this :D

Cheers.

I'll try that when I get home (I'm at work now):lolflag:

---

