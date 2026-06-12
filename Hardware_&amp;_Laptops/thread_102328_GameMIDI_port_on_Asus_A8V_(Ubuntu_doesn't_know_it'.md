---
title: "Game/MIDI port on Asus A8V (Ubuntu doesn't know it's there)"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by mrowth on 2005-12-11
Kubuntu 5.10 on an Asus A8V Deluxe "Wi-Fi Edition" mainboard, with the included MIDI/Gameport/USB bracket plugged in...

How do I get this to work for both my joystick (something big and bulky, apparently unashamed to be calling itself a "Fanatec Aggressor") and MIDI?

[quote="KDE joystick Control Module"]
"No joystick device automatically found on this computer. 
Checks were done in /dev/js[0-4] and /dev/input/js[0-4]
If you know there is one attached, please enter the correct device file.[/quote]

What *is* the correct device file? Can I create it (how)?

Haven't tried MIDI yet (one step at a time)...

Some potentially relevant lsmod output: 

```
Module                  Size  Used by
snd_mpu401              6344  0
analog                 10528  0
snd_via82xx            25792  1
gameport               14472  2 analog,snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_mpu401_uart         6784  2 snd_mpu401,snd_via82xx
snd_bt87x              13768  1
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_via82xx,snd_ac97_codec,snd_bt87x,snd_pcm_oss
snd_page_alloc         10120  3 snd_via82xx,snd_bt87x,snd_pcm
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  18 snd_mpu401,snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
via82cxxx              12188  1
```

---

### Post by pjbgravely on 2006-04-03
gameport               14472  2 analog,snd_via82xx

Looks like the gameport is enabled, now you need to get the joystick drivers to load. Try reading this.

[http://ubuntuforums.org/showthread.php?t=55173]("http://ubuntuforums.org/showthread.php?t=55173")

Paul

---

