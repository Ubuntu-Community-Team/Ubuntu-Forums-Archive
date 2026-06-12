---
title: "How to Remove and Re-add Sound Card to Ubuntu?"
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by kah00na on 2008-04-04
In windoze, I can open the device manager, right-click on the sound card, and click uninstall.  I can then go into "add new hardware" and let it run and it will re-find the sound card and reconfigure and it starts working again. 

How can I do something similar to this in Ubuntu?  The other day, while watching a movie, the sound cut out of one ear then the other.  After that, the sound quit working all together.  I ended up re-installing Ubuntu to get it to work. 

How can I remove and re-add hardware in Ubuntu?

---

### Post by TheLions on 2008-04-04
you can remove it by removing packages e.g. to remove ATI  driver you have to remove fxglr package, to uninstall sound you have to remove alsa. Also if you wish on to disable it you can remove/modify  its config files

---

### Post by prshah on 2008-04-04
> **kah00na said:**
> 
How can I remove and re-add hardware in Ubuntu?

```
sudo rmmod somedrivername
sudo modprobe somedrivername

```

To find the driver for your sound card, use ```
lsmod | grep -i snd
```

---

### Post by kah00na on 2008-04-07
Which one(s) of these would I "rmmod" and "modprobe"?:

```
$ lsmod | grep -i snd
snd_intel8x0           34332  1
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
$
```

---

