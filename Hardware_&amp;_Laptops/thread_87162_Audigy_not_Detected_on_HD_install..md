---
title: "Audigy not Detected on HD install."
date: 2005-11-07
forum: Hardware &amp; Laptops
---

### Post by CrazyCanuck00 on 2005-11-07
I'm a new convert to Ubuntu (Formerly a Gentoo-er), and I'm having an ugly problem with my soundcard.  While my card is detected fine on the Live CD, it isn't detected at all on my HD install.  Nothing is listed in my /proc/asound/cards file, nor will ALSAMIXER even load, as there's no devices.  I've set the emu10k1 module to load on startup, and it's loaded after startup, along with lspci recognizing the card, but still no luck.  Any suggestions?  It's early enough that a reinstall wouldn't make me cry at all, simply because all of my personal sata is on another hard drive.  

Thanks in advance!

---

### Post by Teroedni on 2005-11-07
I would say try to reinstall or do a kernel compiling

---

