---
title: "Problem with C-Media CMI8738 Sound chip (Trust SC-5250 card)"
date: 2009-07-29
forum: Hardware
---

### Post by Sir-Archimedes on 2009-07-29
Hello,

I cannot get my Trust SC-5250 sound card (C-Media CMI8738 (model 55) chipset) to run in Ubuntu 9.04.

In the audio settings dialog I see the card but I cannot find a suitable device to get the sound (using S/PDIF) to my receiver. If I try the "... PCI DAC/ADC (ALSA)" device, Ubuntu tells me that the audio device could not be opened for playback.

Has anybody got a clue how to get this soundcard up and running in digital mode via S/PDIF?

Thanks and regards,
sir-archimedes

aplay -l shows (in German):
 aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: CMI8738 [C-Media CMI8738], Gerät 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: CMI8738 [C-Media CMI8738], Gerät 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: CMI8738 [C-Media CMI8738], Gerät 2: CMI8738-MC6 [C-Media PCI IEC958]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: Intel [HDA Intel], Gerät 0: ALC888 Analog [ALC888 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: Intel [HDA Intel], Gerät 1: ALC888 Digital [ALC888 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

---

