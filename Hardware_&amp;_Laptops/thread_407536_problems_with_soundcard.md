---
title: "problems with soundcard"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by Bart Ellebaut on 2007-04-12
I recently installed ubuntu on my pc. But I've got a problem with my sound.
everything is installed (I guess), but still no sound.
I've got xmms installed and stuff, and it play's, but no sound.
Does anyond have any idea how this is possible, or what I have to do?

(ps: any possibility to instal i-tunes on ubuntu?)

thx
Bart

---

### Post by renzokuken on 2007-04-12
do you know what sound card / chipset you have.

have a look at the output of ```
lspci
```

may have to update to a newer version of alsa-driver, thats how i solved my sound problem which sounds exactly the same as yours.

---

### Post by Bart Ellebaut on 2007-04-12
I know the one I've got, and I followed the ubuntuguide.
I've plugged in my pc-boxes, and now I've got sound, but not the original laptopboxes.

soundcard:00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)

---

