---
title: "I have sound in Gnome, but not in apps"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by charlesb on 2005-04-20
I have a strange problem: sound is OK in gnome interface (e.g. I hear the login/logout sounds), but when I start RythmBox or Totem, I get the following message :

**OSS device "/dev/dsp" is already in use by another program**

When I kill esd and relauch it, I get the startup sound.
I edited my /etc/esound/esd.conf as in the "Howto: about sound in Hoary & Linux".
"lsof /dev/dsp" output nothing, and here is the output of lsmod|grep snd :
```
snd_cmipci             35904  1
snd_pcm_oss            56676  0
snd_mixer_oss          20288  2 snd_pcm_oss
snd_pcm               102348  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           12096  1 snd_cmipci
snd_timer              26184  2 snd_pcm,snd_opl3_lib
snd_hwdep              10248  1 snd_opl3_lib
gameport                4992  1 snd_cmipci
snd_mpu401_uart         8192  1 snd_cmipci
snd_rawmidi            26528  1 snd_mpu401_uart
snd_seq_device          9744  2 snd_opl3_lib,snd_rawmidi
snd                    58600  10 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              11360  2 snd
```

My soundcard is CMI8738, and I'm on AMD64 Hoary.

Thanks for your help!

---

### Post by ZeroVerteX on 2005-04-20
Follow these instructions. Worked for me in XFCE and in Gnome. Also will allow multi-threaded sound (playing 2 sounds at the same time).

[http://www.ubuntuforums.org/showthread.php?t=8882](http://www.ubuntuforums.org/showthread.php?t=8882)

Good luck.

---

### Post by charlesb on 2005-04-23
Thank you for the link, but I still get the same errors :neutral:  :neutral:

---

### Post by Spif on 2005-04-23
Installing libsdl1.2debian-all solved my sound problems.

---

### Post by charlesb on 2005-04-24
[QUOTE=Spif]Installing libsdl1.2debian-all solved my sound problems.[/QUOTE]
 Unfortunately this didn't solve it...

---

### Post by charlesb on 2005-04-27
Still no sound in my Ubuntu.... anyone?

---

