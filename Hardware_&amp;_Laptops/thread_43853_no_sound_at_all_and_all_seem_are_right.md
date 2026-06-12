---
title: "no sound at all and all seem are right"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by manou on 2005-06-23
Hi, I'm installing a GNU/Linux system on a new computer.
In windows the sound works right, so there is no technical problem. I installed win to test the HW.
I dont have any sound at my system.



This is my sound card:
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

This is the sound modules:
silvia@semprom:~$ lsmod | grep snd
snd_via82xx            25248  1
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd
gameport                4608  2 snd_via82xx,analog

I'm using:silvia@semprom:~$ uname -a
Linux semprom 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
with a kubuntu distribution.

Previously i've installed ubuntu, but to since i have read thet kubuntu works with arts that is different i tried to install kubuntu to see if the sound is going to work, but not.
I also have done all the steps described in documents as:
[http://ubuntuforums.org/showthread.php?t=26567&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=26567&page=1&pp=10)

But no sound in my box.
The main problem is that is not for me this thing. It's a computer i have to deliver tomorrow and i would like to install gnu/linux to try this friend start to work with linux, but if there is no sound problably she is not going to want linux.
In my system i have sound with alsa in a debian sarge and the config files i thing there are almost the same, so i'm really lost about what can happend.
I try to find any hw problem with this card in linux but i don't find. In fect there are people with this sound card enyoing his/her sound in gnu/linux...

Please any guide will be appreciate. ](*,)  ](*,)

---

### Post by Martin Witte on 2005-06-23
Maybe this hint does it for you as well: [http://www.ubuntuforums.org/showthread.php?t=39109](http://www.ubuntuforums.org/showthread.php?t=39109)

---

