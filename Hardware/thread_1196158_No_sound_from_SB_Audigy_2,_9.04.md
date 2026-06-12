---
title: "No sound from SB Audigy 2, 9.04"
date: 2009-06-24
forum: Hardware
---

### Post by rocdoc on 2009-06-24
Just loaded 9.04 on this box that has a built in Via sound chip (disabled in BIOS) and a much better SoundBlaster Audigy 2 card. The Via chip, despite being shut off in BIOS is recognized and works fine. The Audigy 2 chip is also recognized but no sound whatsover. Yes, I have tried the Analog/Digital switch as suggested by many but that does not work.


Relevant output from "lspci"
```

00:0e.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```
Relevant output from "lsmod":
```

snd_emu10k1_synth      14336  0 
snd_emux_synth         40832  1 snd_emu10k1_synth
snd_seq_virmidi        13440  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           144288  3 snd_emu10k1_synth
snd_util_mem           12288  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15108  2 snd_emux_synth,snd_emu10k1
snd_via82xx            32152  3 
snd_via82xx_modem      19336  0 
snd_mpu401_uart        15104  1 snd_via82xx
snd_seq_dummy          10756  0 
snd_ac97_codec        112292  3 snd_emu10k1,snd_via82xx,snd_via82xx_modem
snd_seq_oss            37760  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_seq_midi           14336  0 
snd_seq_midi_event     15104  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
ppdev                  15620  0 
snd_seq                56880  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                82948  5 snd_emu10k1,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
nvidia               7097928  34 
snd_rawmidi            29696  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi
snd_seq_device         14988  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
pcspkr                 10496  0 
serio_raw              13316  0 
snd_timer              29704  3 snd_emu10k1,snd_seq,snd_pcm
snd_page_alloc         16904  4 snd_emu10k1,snd_via82xx,snd_via82xx_modem,snd_pcm
i2c_viapro             15892  0 
emu10k1_gp             10752  0 
via_agp                16256  1 
snd                    62628  26 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd
_hwdep,snd_via82xx,snd_via82xx_modem,snd_mpu401_uart,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_rawmidi,snd_seq_device,snd_timersoundcore              15200  1 snd

```

Further information obtained through the alsa troubleshooting script specific to my system can be found here:

[http://www.alsa-project.org/db/?f=e5a5d81c76236f93648631708549c98c48fac70d](http://www.alsa-project.org/db/?f=e5a5d81c76236f93648631708549c98c48fac70d)

All the right modules appear to be loaded. I have ensured the volume control is set to the Audigy chip, as is the Sound Server. Still no luck.

Any ideas greatly appreciated.

Larry

EDIT: Solution below

---

### Post by rocdoc on 2009-06-24
Here we go again solving my own problems....it took two days but I learned a lot. It seems alsa and Pulse Audio could not cope with the two sound chips in my system and the onboard chip was being chosen in preference to the outboard Audigy one (even though the latter was told to be Device 0 and the former one was shut off in BIOS!). 

So the solution was to completely disable the onboard chip by blacklisting its modules. Type "lsmod" to find the modules related to the hardware you want to disable. Then add the line(s): "blacklist nameofmodule" to the /etc/modules.d/blacklist.conf file.

---

### Post by kostkon on 2009-06-24
> **rocdoc said:**
> Here we go again solving my own problems....it took two days but I learned a lot. It seems alsa and Pulse Audio could not cope with the two sound chips in my system and the onboard chip was being chosen in preference to the outboard Audigy one (even though the latter was told to be Device 0 and the former one was shut off in BIOS!). 

So the solution was to completely disable the onboard chip by blacklisting its modules. Type "lsmod" to find the modules related to the hardware you want to disable. Then add the line(s): "blacklist nameofmodule" to the /etc/modules.d/blacklist.conf file.
Actually, you only had to install the *PulseAudio Device Chooser* utility (using Synaptic) and set your *Audigy* as the default audio device in your system; simple and easy.

Obviously, *PulseAudio* and *Alsa* can cope with many audio devices in a system.

For more info check [this thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by rocdoc on 2009-06-24
> **kostkon said:**
> Actually, you only had to install the *PulseAudio Device Chooser* utility (using Synaptic) and set your *Audigy* as the default audio device in your system; simple and easy.


Actually not. I tried the device chooser and it did not work for me.

---

