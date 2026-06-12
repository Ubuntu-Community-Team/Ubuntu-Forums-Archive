---
title: "HP 15-ay078TX Ubuntu 14.04 LTS no sound"
date: 2017-02-04
forum: Hardware
---

### Post by sandeep21 on 2017-02-04
Good day All,
It has been over two months but the sound in my HP 15-ay078TX Laptop remains non working. Tried everything below:
a) checking if volume is mute/force-reloading alsa
b) disabling [COLOR=#000000]speech[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]dispatcher
[/COLOR]c) Running and selecting correct device in alsamixer
d) R[COLOR=#282828][FONT=helvetica]einstalling Alsa and Pulse Audio
[/FONT][/COLOR]e) Opening[COLOR=#2A2E2E][FONT=&quot] /etc/modprobe.d/alsa-base.conf in sudo mode [/FONT][/COLOR][COLOR=#2A2E2E][FONT=&quot]and adding following two lines:[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&quot]options snd-hda-intel model=eapd probe_mask=1 position_fix=1[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&quot]options snd-hda-intel model=laptop position_fix=1 enable=yes.

[/FONT][/COLOR]What should I do?

Please help.
:(

---

