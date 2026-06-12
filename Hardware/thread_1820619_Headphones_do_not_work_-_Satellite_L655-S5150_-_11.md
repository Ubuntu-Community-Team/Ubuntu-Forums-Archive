---
title: "Headphones do not work - Satellite L655-S5150 - 11.04 32bit"
date: 2011-08-07
forum: Hardware
---

### Post by floggy on 2011-08-07
Did "gksu gedit /etc/modprobe.d/alsa-base.conf" in the terminal.

Added "options snd-hda-intel model=thinkpad" on the bottom line.

Saved it.

Rebooted.

Headphones work now.

Hope this helps someone.

---

