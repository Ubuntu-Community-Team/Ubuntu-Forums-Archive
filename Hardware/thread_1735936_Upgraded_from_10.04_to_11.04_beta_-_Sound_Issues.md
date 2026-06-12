---
title: "Upgraded from 10.04 to 11.04 beta - Sound Issues"
date: 2011-04-21
forum: Hardware
---

### Post by Mr. Tux on 2011-04-21
A couple of days ago I upgraded from 10.04 to 10.10 to 11.04 beta.  Today I noticed that my built in mic no longer works, and sound isn't routed to my headphones when I plug them in.

I noticed that my chipset of my card is also different between 10.04 and 11.04.

10.04
Card: HDA Intel PCH
Chip: Intel ID 2805

11.04
Card: HDA Intel PCH
Chip: Intel CougarPoint HDMI

I've attached the output of lsmod and lshw for my system.

Thoughts?

---

### Post by chrisHHde on 2011-07-21
Same with me! Mic doesn't work.... :-( (Still in released version 11.04)

I played around a little with alsamixer and some kernel settings but to no avail....

Tried /etc/modprobes/alsa-base.conf:
options snd-hda-intel model=laptop position_fix=1 enable=yes
(variations of that)

Tried acpi_osi=Linux in /etc/default/grub (function keys don't work either)

Looked this sound chip up in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz and /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz, but didn't find it appropriately.

My laptop is an Asus U30SD-RO068V laptop.

Anyone solved this problem?? (Or even having it, except for me and Mr Tux)

---

