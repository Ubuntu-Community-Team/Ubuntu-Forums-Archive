---
title: "Ubuntu Studio Soundcard not detected"
date: 2008-05-02
forum: Hardware
---

### Post by TPS0852 on 2008-05-02
Hi There,
I've got a rusty IBM Aptiva (AMD K6 299MHz, 256 MB RAM) with an onboard audiocontroller (Crystal Audio ???).

Ubuntu Studio 8.04 LTS up and going,
but no sounds. (This would be very crucial, as I'm about to test this platform for DAW use !!!)

In terminal:
--> asoundconf list says, that no soundcards are detected, but
--> lsmod |grep snd produces some kind of info (beginning with snd)

--> latest ubuntu-modules are installed (checked through Synaptic)

I've also got a Terratec Base 1/64 soundcard plugged in,
but it won't show up either.

Grateful For Any Help...
Yours,
toni S / Finland

---

### Post by Vermind on 2008-05-02
Hi,
please post the output of lspci.
also, [ALSA sound card matrix]("http://http://www.alsa-project.org/main/index.php/Matrix:Main#ALSA_SoundCard_Matrix") is a good place to start.

---

