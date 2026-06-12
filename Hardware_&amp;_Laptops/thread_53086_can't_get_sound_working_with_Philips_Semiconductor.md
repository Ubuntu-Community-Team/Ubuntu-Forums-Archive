---
title: "can't get sound working with Philips Semiconductors SAA7134"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by commie_coder on 2005-07-30
hi all,

can't get sound working with "Multimedia controller: Philips Semiconductors SAA7134" on a HP Pavillion workstation running kde.

i get the following error from kde control center:

[INDENT]
Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (No such file or directory)
The sound server will continue, using the null output device.[/INDENT]

some more information:

[INDENT]# lsmod | grep sound
soundcore               9824  1 saa7134

# lspci | grep Multimedia
0000:03:05.0 Multimedia controller: Philips Semiconductors SAA7134 (rev 01)
[/INDENT]
the volume icon in the task bar has a red cross on it, and the tool tip reads:

[INDENT]mixer cannot be found[/INDENT]

any ideas?

tia

justin

---

