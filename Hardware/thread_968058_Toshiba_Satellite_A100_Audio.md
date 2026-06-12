---
title: "Toshiba Satellite A100 Audio"
date: 2008-11-02
forum: Hardware
---

### Post by djcrazymonkey on 2008-11-02
Hi,
I have a Toshiba Satellite A100 SK4 (with an Intel 945 chipset) and have just installed Ubuntu 8.10 on it. Everything seems to be working fine, and better than 8.04 (font DPI settings, 3945 wifi card, compiz), but once the system enters suspend, sound no longer works.

I know this is a quite common issue with Intel HDA laptops, and I've tried the following things to try to correct it, as suggested by others online:
*modify the alsa-base settings, adding module=toshiba, auto, etc.
*running a script that restarts alsa on resume, but this crashes any app that was making sound at the time of suspend
*switching back to OSS, but this makes the volume too quiet to be usable.

And nothing works. Any suggestions would be very much appreciated. Thanks.

---

### Post by djcrazymonkey on 2008-11-02
Bump please? :)

---

### Post by djcrazymonkey on 2008-11-05
No one can help? :(

---

### Post by rhomany on 2008-11-22
Just discovered exactly the same problem. It worked find on Hardy but Ibex is just telling me no audio drivers are found.

---

