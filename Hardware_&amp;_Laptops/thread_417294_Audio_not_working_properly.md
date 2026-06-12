---
title: "Audio not working properly"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by GwydionThendon on 2007-04-21
Hi,
I recently installed Ubuntu 7.04 on my desktop and I'm having problems with audio devices. In fact I've got 2 audio peripherals: one integrated on the motherboard and a Sound Blaster live 5.1. I usually disable from the bios the integrated one but this time I forgot to do that before installing Ubuntu. The consequence is that Ubuntu uses that as default audio device. The problem is that even though I disabled the integrated audio device now I can't hear any sound from the Sound Blaster. The only sound I can hear comes from skype, since I selected from the options the Sound Blaster as audio device. Moreover I noticed that the system in some way still recognises more that one audio device. Is there a way to disable an audio card via software or specify the correct one?

Thanks

---

### Post by xflbret on 2007-04-21
me too

---

### Post by Rmantingh on 2007-06-19
Setting your default card is done by following in a terminal:
$ asoundconf list
$ asoundconf set-default-card xxxxx

The first command lists the available soundcards it found
and the second can be used to set the default (replace xxxxx
with the name of one of the soundcards listed.
Hope this helps.

---

### Post by truck87bp on 2007-06-19
I also was having audio problems and found an update to Skype on Digg.  Uninstalled my current Skype and installed the new Beta Skype 1.4.0.74 and my sound problem cleared up.

---

