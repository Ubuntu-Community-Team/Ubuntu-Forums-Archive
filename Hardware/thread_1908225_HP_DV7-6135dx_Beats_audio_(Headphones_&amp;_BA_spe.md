---
title: "HP DV7-6135dx Beats audio (Headphones &amp; BA speakers play at the same time)"
date: 2012-01-13
forum: Hardware
---

### Post by Sxynerd on 2012-01-13
I have an HP DV7 with Beats audio and one of the issues I'm having with it is when I plug in my headphones, one of my PC's BA speakers still plays music.  I think it is the sub under the PC.  The rest of them shut off.

Any help would be great.

Ubuntu 11.10

---

### Post by Sxynerd on 2012-01-13
Anyone?
:confused:

---

### Post by Sxynerd on 2012-01-15
Please Help

---

### Post by Sxynerd on 2012-01-16
Anyone?

---

### Post by nardusg on 2012-01-18
got the same issue and don't have a solution yet...

---

### Post by MoreOrLess on 2012-01-18
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Sxynerd on 2012-01-18
Thanks for the response

[http://www.alsa-project.org/db/?f=823ab66332bb28b2d1ac14dc641d1132af6f7cb2](http://www.alsa-project.org/db/?f=823ab66332bb28b2d1ac14dc641d1132af6f7cb2)

> wolvee@wolvee--dv7:~$ cd ~/
wolvee@wolvee--dv7:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2012-01-18 10:17:02--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2012-01-18 10:17:06--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: 27247 (27K) [text/plain]
Saving to: `alsa-info.sh'

100%[======================================>] 27,247      51.2K/s   in 0.5s    

2012-01-18 10:17:09 (51.2 KB/s) - `alsa-info.sh' saved [27247/27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)


---

### Post by MoreOrLess on 2012-01-18
Has anyone played with different outputs in the volume control?

Also, I would try different models in /etc/modprobe.d/alsa-base.conf.
```
gksu gedit /etc/modprobe.d/alsa-base.conf
``` For example, add the following line to the end of the file:
```
options snd-hda-intel model=ref
```Then, restart alsa:
```
sudo alsa force-reload
```If it doesn't help, repeat the process changing the model keyword (here is the list for your codec):

```
  ref        Reference board
  mic-ref    Reference board with power management for ports
  dell-s14    Dell laptop
  dell-vostro-3500    Dell Vostro 3500 laptop
  hp        HP laptops with (inverted) mute-LED
  hp-dv7-4000    HP dv-7 4000
  auto        BIOS setup (default)
```

---

### Post by Sxynerd on 2012-01-18
Thanks, I have tried changing the sound output setting with no luck.

I tried adding the first line of code you suggested with no change.  When I plug in the headphones the Sound output does change to "Headphones" but the Sub speaker is still putting out sound.

I don't know I am supposed to do with the second set of commands.  (Where I'm supposed to put them.)

Thanks again for your help.

---

### Post by MoreOrLess on 2012-01-18
You need to restart alsa with that command before the line takes effect. That last block means try the options line with a different model= (model=hp, model=hp-dv7-4000), then restart alsa after each new model you try.

---

