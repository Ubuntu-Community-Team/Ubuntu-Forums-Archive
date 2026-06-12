---
title: "Logitech Wireless Music System"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by bayonetblaha on 2007-09-16
I'm trying to find drivers for the Logitech Wireless Music System, a USB device that transmits sound to a receiver elsewhere.  I don't really know where to look. Where should I look for these drivers? Does anyone know how to make this device work?

---

### Post by gautada on 2007-09-16
Since it does not require any special software it might work just fine and a plain USB device.  Have you tried it yet?

---

### Post by bayonetblaha on 2007-09-16
this just got more interesting.

I googled the lsusb entry for the logitech device (ID 0b7a:0100 Zeevo, Inc. ) and the sole hit was a comment on a blog where someone was complaining about xmms being considered for removal from ubuntu:

"too bad if xmms is going away. it's my only option when I use my Logitech wireless usb-soundcard ( Bus 003 Device 006: ID 0b7a:0100 Zeevo, Inc.) since so far I haven't found another music player that can chooce the output device without running alsaconf or changing the default output device for all sound."

how can I make other programs (i.e. firefox) use my new device as their soundcard? Is there an easy way to control what uses what?

---

### Post by bayonetblaha on 2007-09-16
thanks gautada,

yeah, apparently it was working, I just didn't know how to designate it for audio output

---

### Post by bayonetblaha on 2007-09-16
for anyone else who comes across this looking for USB Logitech Wireless Music System linux compatability, Amarok does the same thing as XMMS listed above, just put the same value into "stereo" where "default" is in the preferences as XMMS is generating when you select the Logitech device for ALSA output.

questions to [email]nelson.blaha@gmail.com[/email] on that

still looking for help on how to control what program uses what device, though

---

