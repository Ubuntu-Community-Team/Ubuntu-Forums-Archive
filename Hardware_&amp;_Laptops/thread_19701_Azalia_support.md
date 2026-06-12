---
title: "Azalia support ???"
date: 2005-03-13
forum: Hardware &amp; Laptops
---

### Post by milou on 2005-03-13
I want to use a 9860 Sager laptop with azalia sound module. So I installed a 2.6.10 kernel, compiled the 1.0.8 version from alsa with alsa-source and installed it.
But if I try to do /etc/init.d/alsa start it fails and a 'modprobe snd-azx' (the module for the sound chip) I get a dump of several line telling "azx_get_response timeout"
and then
"hda_codec" : no AFG node found ... azx : no codes initialized

I don't understand because I saw on the net that most people got it working with gentoo systems with kernel 2.6.10 and alsa 1.0.8 ....

Eric

---

### Post by JoshGreen on 2005-04-13
Isn't the module snd_hda_intel?  At least thats the one I'm using.  I can get sound output, but I'm having various other problems:
- No output with headphones (yes "Headphone" is unmuted and turned up)
- OSS programs using MMAP mode are failing (quake3, xmms, etc)
- Some clicking in audio output (sampling rate problems?)

Hopefully I can get these resolved soon :(

---

