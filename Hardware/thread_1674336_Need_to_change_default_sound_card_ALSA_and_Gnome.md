---
title: "Need to change default sound card ALSA and Gnome"
date: 2011-01-23
forum: Hardware
---

### Post by dishbert on 2011-01-23
I've searched high and low with no success, but there just has to be a way to do this.

Using Lucid:

chris@PC-Linux:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcf78000 irq 21
 1 [CMI8770        ]: CMI8738-MC8 - C-Media CMI8770
                      C-Media CMI8770 at 0xd800, irq 19


It is card 0 (supposedly the default device?) that I want to use, but when I select "default" in the alsa-mixer gui, the display changes to C-Media, and I can't get any output from the NVidia card.

Suggestions?

---

