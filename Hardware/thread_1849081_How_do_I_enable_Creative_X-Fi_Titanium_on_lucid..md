---
title: "How do I enable Creative X-Fi Titanium on lucid."
date: 2011-09-23
forum: Hardware
---

### Post by Wirebiter on 2011-09-23
Hi

I'm having some trouble getting my X-Fi Titanium sound card to work. From what I can tell the drivers are installed out of the box but they are not loaded and the card is not shown in the sound settings menu.

Output from lspci -k
```

05:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)
    Kernel modules: snd-ctxfi

```Any ideas?

---

### Post by wolfen69 on 2011-09-23
There are linux drivers for the titanium at the creative website.

---

### Post by Wirebiter on 2011-09-24
I first tried to use them, but when I run make I get a fatal error, saying that sound/driver.h cannot be found. From a thread on this forum someone pointed out that the drivers where already installed out of the box, meaning that there's need to compile them myself. 

If that could work, does anyone know how to find the driver.h file?

---

