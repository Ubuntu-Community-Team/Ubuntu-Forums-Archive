---
title: "Alsa install Acer Aspire 5530"
date: 2009-02-23
forum: Hardware
---

### Post by matej123 on 2009-02-23
Hi everyone.
First of all: I know that there are several threads about how to install the alsa driver, but nothing realy helps.

I have an acer aspire 5530 with a realtek alc888 soundchip. The sound is just coming out through the internal speaker. The headphone jack is not working.

here is what cat /proc/asound/cards post:

[I]matej@matej-laptop:~$ cat /proc/asound/cards 
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf0500000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xcfeec000 irq 19


matej@matej-laptop:~$ head -n 1 /proc/asound/card0/codec* 
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC888

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06[/I]

So i tried to change the file **/etc/modprobe.d/alsa-base** by typing **options snd-hda-intel model= acer** in the last line.

The result was, that there was no sound. I could not open the alsamixer.


[B]Is there any instruction how to install the ALSA-Driver on the Acer Aspire, so i could use the headphone jack??

I hope that someone can help me![/B]

---

### Post by maron on 2009-03-13
Try uncheck surround in sound options opened by click on tray icon sound.

---

