---
title: "No sound VIA 8235 ubuntu serve 14.04.4 i386"
date: 2016-07-18
forum: Hardware
---

### Post by herkow on 2016-07-18
Hi guys, I've been struggling with this for three days... I'm lost now...
I've done everything I've read online, and nothing happened.
Ubuntu server 14.04.4 4.2.0-27-generic


No matter what, I can´t get any sound from this on-board sound card. I've noticed that most people say this is a very, very bad sound card for GNU/Linux. 


This is the report from "alsa information script":


[http://www.alsa-project.org/db/?f=c9...91c432f22d23e1](http://www.alsa-project.org/db/?f=c9...91c432f22d23e1)




```

hlk@NMP:~$ cat /proc/asound/cards
 0 [V8235          ]: VIA8233 - VIA 8235
                      VIA 8235 with VT1616i at 0xe000, irq 22
hlk@NMP:~$

```




```

hlk@NMP:~$ lsmod | grep snd
snd_wavefront          36864  0
snd_cs4236             32768  0
snd_via82xx            24576  0
snd_opl3_lib           20480  2 snd_wavefront,snd_cs4236
snd_ac97_codec        106496  1 snd_via82xx
snd_hwdep              16384  2 snd_wavefront,snd_opl3_lib
snd_wss_lib            28672  2 snd_wavefront,snd_cs4236
ac97_bus               16384  1 snd_ac97_codec
snd_pcm                94208  4 snd_via82xx,snd_ac97_codec,snd_wss_lib,snd_cs4236
snd_mpu401_uart        16384  3 snd_via82xx,snd_wavefront,snd_cs4236
snd_rawmidi            28672  2 snd_wavefront,snd_mpu401_uart
snd_timer              24576  3 snd_wss_lib,snd_pcm,snd_opl3_lib
snd_seq_device         16384  2 snd_rawmidi,snd_opl3_lib
snd                    69632  12 snd_via82xx,snd_ac97_codec,snd_hwdep,snd_timer snd_wss_lib,snd_pcm,snd_rawmidi,snd_wavefront,snd_mpu401_uart,snd_seq_device,sn _cs4236,snd_opl3_lib
soundcore              16384  1 snd
gameport               16384  2 snd_via82xx,ns558
hlk@NMP:~$

```




```

hlk@NMP:~$ lspci | grep audio
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
hlk@NMP:~$

```




Alsamixer shows everything ok. 


I'm setting up a network music player with mpd, and sound is a little bit... Neccesary...


Hope you can help me...

---

### Post by leozinho29_eu on 2016-07-20
I had issues with a VIA VT1818S ( [https://ubuntuforums.org/showthread.php?t=2317802](https://ubuntuforums.org/showthread.php?t=2317802) ). I had sound from the rear jacks only. There was a configuration in BIOS which forced the identification of the slots and then it worked.

---

### Post by Yellow Pasque on 2016-07-21
You link to the alsa info got messed up.

---

