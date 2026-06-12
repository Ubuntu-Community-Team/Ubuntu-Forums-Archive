---
title: "Lenovo s10e Skype problems."
date: 2009-05-20
forum: Hardware
---

### Post by Donnut on 2009-05-20
I have searched the forums and have not found a solid answer to this, the internal mic doesn't work with skype.  I have tried all combinations of sound devices, but none seem to work.  Anybody had success with this?

---

### Post by bolbo on 2009-05-23
Try this:
sudo gedit /etc/modprobe.d/alsa-base.conf
add at the end:
options snd-hda-intel model=basic
save and reboot
This should make the mic working. Be sure to activate it in the volume control applet.

Sergio

---

