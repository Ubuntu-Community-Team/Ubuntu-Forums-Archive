---
title: "No sound from headphones with ALC883"
date: 2009-01-18
forum: Hardware
---

### Post by kenstad on 2009-01-18
Hi all,
I realize that similar threads exist, but none seem to suggest a solution that works for me. I get sound from the notebook speakers, but no sound from the headphones jack. In addition the notebook speakers do not mute when I plug in the headphones. 

I have an MSI barebook notebook with a version of Intel HDA (Realtek ALC883), no S/PDIF, (I have tried to specify different models in /etc/modprobe.d/alsa-base, such as 3stack-6ch etc.). I have  ubuntu 8.10, the latest version of Alsa drivers (1.0.18), and there is no clutter on the computer since I reinstalled ubuntu yesterday, partly in order to try to solve the headphones issue. No luck so far.

I have a volume control in alsa-mixer called 'headphones', but there is no outline for the meter, and it won't let me adjust the volume. I attach a screen dump.

I also attach output from lsmod | grep snd, my alsa-base file (which has some of the changes suggested in some of the threads here). This may also be relevant - I don't know.

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

uname -r
2.6.27-9-generic

I thought the result of the following command was a bit strange (what is LSI Si3054???), but what do I know...

head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC883

==> /proc/asound/card0/codec#1 <==
Codec: LSI Si3054


Has anyone got any idea?

---

### Post by jerbroo on 2009-03-04
I appreciate the detail on this.  Did you ever find a solution?

---

### Post by jerbroo on 2009-03-05
Well, my headphone jack now works and is controlled by the master volume just like I wanted.  The speakers automatically mute when headphones are plugged in too.

***specs and notes***
running kernel: 2.6.24-23-generic
current alsa: 1.0.19
laptop: Acer Aspire 5572NWXCi (three jacks in front including spdif headphone combo).  
sound card: Intel HDA, ALC883

**NOTE: There is still NO working headphone volume slider in alsamixer.
 
>aplay -l
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
...

NOTE both digital and analog devices.


***the fix for me***
Here's what did the trick and fixed it...  after much fiddling.

1. Read through this short how to on sound troubleshooting.

[http://ubuntuforums.org/showthread.php?t=205449&highlight=headphone+volume](http://ubuntuforums.org/showthread.php?t=205449&highlight=headphone+volume)
 
2. Actually removed and purged alsa as the above guide states.  ...might not be needed.

3. Install latest Alsa lib, utils and drivers with this howto:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

4. set this option in /etc/modprobe.d/alsa-base at the bottom of the file:

options snd-hda-intel model=acer-aspire

NOTE: If you don't have spdif output use..
options snd-hda-intel model=acer


5. reboot...   plug in my cheapo headphones and smile when I went nearly went deaf from the awesome sounds of Mr. Jack White.


HTH!
 Jeremy Brooks
[Austin E-Commerce and Search Marketing]("http://www.easyadwordstuner.com")

---

### Post by acracker on 2009-03-06
Thank you so much, this solved my problem! I went about it slightly differently though as I didn't have to do any installing/removing of applications.

What I did:
```

head -n 1 /proc/asound/card0/codec*

```

The output I got was:
```

Codec: IDT 92HD73C1X5

```

Then I typed in:
```

zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

```

and scrolled down to the section titled "Module snd-hda-intel". Under this section I scrolled down until I found a model number as close as I could find to mine, this turned out to be STAC92HD73*. Directly under this I chose "dell-m6". If you have multiple options under yours, you may have to do some testing to find the right one.

Next, I opened up alsa-base with:
```

sudo gedit /ect/modprobe.d/alsa-base

```
and scrolled down to the bottom and typed:
```

options snd-hda-intel model=dell-m6

```

Then I saved the file, quit gedit and restarted my computer. Now my speakers mute automatically when I plug in headphones. Hope this helps anyone having these problems too.

---

### Post by jerbroo on 2009-03-06
I'm Glad it could help out.

---

### Post by marcelo_gomes on 2009-05-13
Thank you SOOOOOOOO much!!!!!

I've been running around like a madman, trying every single suggestion I've encountered - from simple re-installation to manually compiling alsa - without any luck.
I was almost giving it up, but this thread saved everything!

By the way, so that others with my conf can find this solution (final info in portuguese 'cause this is a Brazilian NB):

head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC883

==> /proc/asound/card0/codec#1 <==
Codec: Motorola Si3054


Notebook Positivo w98
(Sound) Placa de Som HDA INTEL ALC883
(Model) Faricante (importantíssimo, é a opção a ser colocada no modelo): clevo-m70

Incluir no arquivo /etc/modprobe.d/alsa-base a linha (fazê-lo via sudo, p.ex.: sudo emacs /etc/modprobe.d/alsa-base ):
options snd-hda-intel model=clevo-m720

---

### Post by marcelo_gomes on 2009-08-10
> **marcelo_gomes said:**
> Thank you SOOOOOOOO much!!!!!

I've been running around like a madman, trying every single suggestion I've encountered - from simple re-installation to manually compiling alsa - without any luck.
I was almost giving it up, but this thread saved everything!

By the way, so that others with my conf can find this solution (final info in portuguese 'cause this is a Brazilian NB):

head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC883

==> /proc/asound/card0/codec#1 <==
Codec: Motorola Si3054


Notebook Positivo w98
(Sound) Placa de Som HDA INTEL ALC883
(Model) Faricante (importantíssimo, é a opção a ser colocada no modelo): clevo-m70

Incluir no arquivo /etc/modprobe.d/alsa-base a linha (fazê-lo via sudo, p.ex.: sudo emacs /etc/modprobe.d/alsa-base ):
options snd-hda-intel model=clevo-m720

After the last update, my soundcard went completely deaf!
I tried commenting (#) the edited line "options snd-hda-intel model=clevo-m720" and everything worked alright again, even the headphone jack!

I guess from now on there will be no need to to this edit on alsa-base.

---

