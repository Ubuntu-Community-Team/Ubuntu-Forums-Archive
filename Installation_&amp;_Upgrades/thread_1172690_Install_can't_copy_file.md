---
title: "Install can't copy file"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by mrhomiec on 2009-05-28
i have both the CD and DVD of Ubuntu 9.04.
both downloaded, and burned myself,
CD at 8x, and DVD at 4x

checked both for errors, and both passed.
both will get to around 70% of the install, 
and say that a file couldn't be copied over,
that the installation has to quit.

i never had this problem with Ubuntu 8.
i'd use that instead if i knew where i put the disc.

ps, also there's random file that can't be copied over either.
but those let me Retry or Skip them.

specs:
Processor AMD 2ghz
RAM 2GB DDR 3200
hard drive is 80GB

---

### Post by merlinus on 2009-05-28
You might post complete system specs.

---

### Post by albinootje on 2009-05-28
> **mrhomiec said:**
> 
both will get to around 70% of the install

Did you check your hard disk for errors with a long test of gsmartctl and the badblocks command (e.g. sudo badblocks -vv /dev/sda) ? [http://gsmartcontrol.berlios.de/home/index.php/en/Home](http://gsmartcontrol.berlios.de/home/index.php/en/Home)

You also try installing from usb-stick.

---

### Post by Wazoot on 2009-05-28
Try installing from a usb-stick .
Or just download the .iso and re-burn it yourself?

---

### Post by mrhomiec on 2009-05-28
i checked my hard drive with gsmart tool,
and it told me my HDD is healthy.

i setup a USB stick to be bootable,
but now i can't remember my BIOS password
i built it in 2003, and it's Phoenix.

edit: booted thru USB, and still got the same error.

edit: downloaded Ubuntu 8.10, and that installed perfectly.

---

