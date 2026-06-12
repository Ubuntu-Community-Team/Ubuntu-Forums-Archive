---
title: "Broken on-board sound, but SoundBlaster not recognized!"
date: 2009-10-25
forum: Hardware
---

### Post by mheartwood on 2009-10-25
I have no sound. 

I'm using Xubuntu 9.04-x64. It recognizes the onboard AC'97 codec. Unfortunately, the analog outputs on that device don't work.

I have a large number of Sounds cards in stock. None of them seem to be being used when I plug them in. I've tried them on my Windows machine and they do work.

I have several "Model: CT4810", Ensoniq, "SoundBlaster Live". and some I can't read without magnifying glasses.

Where I can I find the equivalent of a device manager so that I can turn off the AC'97 and see if the sounds card which is plugged in is even recognized?

Thanks

---

### Post by IcarusR on 2009-10-25
I suggest you disable onboard sound in the bios.

From a terminal type the following & look for a line listing your sound device.

```
lspci
```

If card is not listed them your system does not recognize it.

---

### Post by markbuntu on 2009-10-25
The SB live cards should work just fine for what they are. You need to reinstall ALSA so the card will be autodetected and the proper driver installed.  After you have installed the card and disabled the on-board card in the bios:

To reload ALSA:

(1) Remove the ALSA packages
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```


(3) Reboot. Do not forget to reboot or it will not work.

After you do that if you have no sound check in the volume control on the panel that the digital (IEC958 for some) output is not selected and the PCM volume is turned up. SBlive, SBlive 64, SBlive 128, audigy and audigy2 users have reported these as the only problems to getting their cards working as far as I have seen in the past few years.

If lspci does not see the card try it in another slot.

---

### Post by mheartwood on 2009-10-26
Thanks! That's seems to have done it!

---

