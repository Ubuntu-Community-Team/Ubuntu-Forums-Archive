---
title: "HowTo: Get your soundcard working on Ubuntu Gutsy [snd-hda-intel]"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by Kalouste on 2008-01-02
**Problem**

[LIST]
[*]No sound at all
[/LIST]

**Hardware**

[LIST]
[*]Laptop: LG P1 Pro Express Dual Laptop
[*] Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
[/LIST]

**Solution**

Open the terminal window and type:

```


**1)** sudo gedit /etc/modprobe.d/alsa-base

In the editor, add the following line at the end of the file:
options snd-hda-intel model=lg

**2)** sudo apt-get install linux-backports-modules-generic

**3)** lspci | grep -i audio
*Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)*

**4)** cat /proc/asound/card0/codec#* | grep Codec
*Codec: Realtek ALC861*

```

_Note 1_ The expected output, for above hardware, is formated in italic.

**Useful links**
[See Method G]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")
[Original description of this method (in portuguese)]("http://silas.theducks.com.br/2007/11/16/audio-no-ubuntu-gutsy-pra-quem-nao-conseguia-uma-ultima-tentativa/")

---

### Post by Kalouste on 2008-01-27
The previous solution was incomplete. Sorry for any inconvenience.

---

