---
title: "Maddening noise from lenovo 3000 n200 on resume"
date: 2008-09-17
forum: Hardware
---

### Post by oybon on 2008-09-17
Almost everything works with this system except.

1) Will go into Hibernate, but on resume Mad wailing noise from speakers (Think rape alarm), Didn't hang around before yanking power to see what else happened.

2) On going into suspend, same mad wailing noise.

System:

Lenovo 3000 n200 core2 with Intel shared graphics
Ubuntu Hardy with all latest updates.

The only none standard alteration is the addition of:

`*options snd-hda-intel position_fix=1 model=lenovo*'

to **etc/modprobe.d/alsa-base** to get sound card working

Any ideas

---

### Post by lio_013 on 2008-09-19
try to mute the mic from the graphic volume control or alsamixer

---

