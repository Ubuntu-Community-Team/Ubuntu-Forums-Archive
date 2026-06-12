---
title: "Medion MD96780"
date: 2009-12-24
forum: Hardware
---

### Post by Aidamina on 2009-12-24
A year ago I've bought a Medion MD96780, which came with windows vista reinstalled. Last week i decided its time for something else, so i decided to install Ubuntu 9.10 on it.

Now everything seems to be working fine except for the sound. By default the sound plays on the speakers, but there's no audio on the headphone jack on the front side of the laptop. 

My laptop comes with a Realtek ALC888 soundchip, and I've tried to use the drivers from the realtek website, but that completely made my sound go away, and the only way i could revert that was my reinstalling Ubuntu again. I've also tried various different alsa settings.

sudo gedit /etc/modprobe.d/alsa-base.conf
then modifying the following line:
options snd-hda-intel model=auto
I've tried various different modeltypes from a list i found elsewhere. One of the model types (targa-dig) did work, as in it produced sound on my headphone jack, but the microphone input doesn't work with that setting. 

When i set the model type to medion i have sound on both my headphone plug and my speakers, and the mic appears to be working too, but I have no way to control the volume of the speakers and the headphones individually, i want to be able to listen to music on my headphones without the speakers producing any sound. I've tried all the sliders in alsamixer, but none of them controls just the speaker or just the headphone channel.

Any help as to debug/configure this, would be greatly appreciated.

---

### Post by RedSingularity on 2009-12-24
To control the channels separately you need to use something like pulseaudio device chooser.  It is located in "Sound and Video".

---

