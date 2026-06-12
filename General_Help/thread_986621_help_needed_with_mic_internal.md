---
title: "help needed with mic internal"
date: 2008-11-18
forum: General Help
---

### Post by verby on 2008-11-18
ok, I have tried everything, well almost everything.
acer 5520, webcam works, sound works, but internal (build in) mic doesn't.
I have tried different settings alsa, puls ... changed input source to internal mic and NOTHING... soundcard HDA nvidia
can someone help?

---

### Post by Th3Professor on 2008-11-18
> **verby said:**
> ok, I have tried everything, well almost everything.
acer 5520, webcam works, sound works, but internal (build in) mic doesn't.
I have tried different settings alsa, puls ... changed input source to internal mic and NOTHING... soundcard HDA nvidia
can someone help?

Mute?

---

### Post by verby on 2008-11-18
mute? no, I have checked this before. I know the hardware works, because I have checked with win partition. Any other ideas?

---

### Post by Th3Professor on 2008-11-19
[COLOR=White]update/upgrade everything
aplay -l
arecord -l
lspci -v
upgrade alsa
configure alsa
alsamixer:
front mic boost: 100
mic boost: 50
capture: 0
capture 1: 0
digital: 97
input source: mic
input source 1: mic
or...[/COLOR][B]
1. right click speaker on icon tray
2. "open volume control"
3. edit "preferences"
4. scroll down and click on capture box
5. close window
6. capture tab now in volume control window, click it
7. max volume, click on mic icon to remove red X
[/B]

---

### Post by verby on 2008-11-19
no luck with this... should I set for pulse or alsa?
Have tried both but no success.

---

### Post by Th3Professor on 2008-11-20
originally I'd have said alsa, though I'm finding more use of pulse these days... continue trying both, though I still try to default at alsa.

[COLOR=Gray]update/upgrade everything
aplay -l
arecord -l
lspci -v
upgrade alsa
configure alsa
alsamixer:
front mic boost: 100
mic boost: 50
capture: 0
capture 1: 0
digital: 97
input source: mic
input source 1: mic
[/COLOR][COLOR=Gray]
[/COLOR]

---

