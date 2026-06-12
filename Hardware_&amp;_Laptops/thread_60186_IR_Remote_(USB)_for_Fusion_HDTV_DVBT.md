---
title: "IR Remote (USB) for Fusion HDTV DVBT"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by absoludity on 2005-08-26
I recently bought a DVICO Fusion HDTV DVB-T card, and managed to get it working with Hoary... very happy with the results (Digital TV in Australia using MythTV).

Followed [Chris Pasco's instructions](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/) to get the Fusion card working.

The only thing that doesn't work is the USB Remote that comes with the card. I've tried the following:
 * Compiling latest LIRC with Chris's patches for Fusion card (when installing it doesn't require any new kernel modules).
 * Recompiling kernel 2.6.10 with patches...

but still when I run lircd and then irw, it doesn't matter how angrily I poke the IR receiver with my remote, pressing buttons all over the place... nothing :(

Is there something simple I'm missing? perhaps a USB IR module or something to load?? I've tried everything I could find but can't find any more info! According to most sites, a USB IR receiver should 'just work'. 

Thanks for any help!

---

### Post by chaumurky on 2005-08-29
[QUOTE=absoludity]I recently bought a DVICO Fusion HDTV DVB-T card, and managed to get it working with Hoary... very happy with the results (Digital TV in Australia using MythTV).

Followed [Chris Pasco's instructions](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/) to get the Fusion card working.

The only thing that doesn't work is the USB Remote that comes with the card. I've tried the following:
 * Compiling latest LIRC with Chris's patches for Fusion card (when installing it doesn't require any new kernel modules).
 * Recompiling kernel 2.6.10 with patches...

but still when I run lircd and then irw, it doesn't matter how angrily I poke the IR receiver with my remote, pressing buttons all over the place... nothing :(

Is there something simple I'm missing? perhaps a USB IR module or something to load?? I've tried everything I could find but can't find any more info! According to most sites, a USB IR receiver should 'just work'. 

Thanks for any help![/QUOTE]
 I have one of those but it's running on my win-boxen. I might plug it in at some stage to see what happens but I'm working on a few other things right now. Perhaps kernel 2.6.12 in breezy will solve some problems. Not long now...

---

### Post by absoludity on 2005-08-30
Thanks chaumurky :) I've got a few ideas to try to get the remote working with 2.6.10, including installing the latest version of libusb... Will let you know if it works.

---

