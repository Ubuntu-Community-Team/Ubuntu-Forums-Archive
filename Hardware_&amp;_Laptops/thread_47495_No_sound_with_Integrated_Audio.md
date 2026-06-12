---
title: "No sound with Integrated Audio"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by flankk on 2005-07-08
No sound from integrated audio, and I can't figure out what the chipset is.

```

# lspci -v|grep audio
# aplay -l
aplay: device_list:200: no soundcards found...

```

---

### Post by az on 2005-07-08
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

---

### Post by flankk on 2005-07-08
[QUOTE=azz][https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)[/QUOTE]

This doesn't help me find out which chipset it is.  I don't understand why lspci wouldn't detect it..

I've gotten a bit further now:

```

# lsmod|grep snd
snd_virmidi             4288  0
snd_seq_virmidi         7296  1 snd_virmidi
snd_seq_midi            8224  0
snd_seq_oss            31488  0
snd_seq_midi_event      7424  3 snd_seq_virmidi,snd_seq_midi,snd_seq_oss
snd_seq                47376  6 snd_seq_virmidi,snd_seq_midi,snd_seq_oss,snd_seq_midi_event
snd_mpu401_uart         7296  0
snd_rawmidi            23072  3 snd_seq_virmidi,snd_seq_midi,snd_mpu401_uart
snd_seq_device          8588  4 snd_seq_midi,snd_seq_oss,snd_seq,snd_rawmidi
snd_dummy               9152  2
snd_pcm_oss            47648  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                82184  2 snd_dummy,snd_pcm_oss
snd_timer              23300  2 snd_seq,snd_pcm
snd                    51300  16 snd_virmidi,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_dummy,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  1 snd_pcm

```

---

