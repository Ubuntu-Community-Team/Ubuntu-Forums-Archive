---
title: "Returning from hibernate = problem"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by simo on 2008-03-07
I have laptop Intel Core 2 Duo, 2 GB RAM, NVIDIA 8600 GT 512 MB, 1 GB swap

I have problem when i'm returning from hibernate. What I want to say is that hibernate is ok, but my computer turns off after some time. I think that my ventilator (cooling) is not working after hibernate so my computer turns off because of heating.

Does anyone had similar problems? Can you give me some help?

Thanx!

---

### Post by -random on 2008-03-07
I also have problems resuming from hibernating/sleep:

My pc starts up, but x doesn't... ctrl+alt+backspace works for me to get the display back, but no sound.

specs: m/b dq35jo, graphics card(not applicable i think,saame situation with intel gma 3100) 8600gt, swap > 4Gb.

---

### Post by kadissie on 2008-03-08
The fan not activating after return from hibernate is a common and serious problem with Ubuntu on laptops. See the [this bug on launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115301").

Be very careful: you can do permanent damage to your computer if it repeatedly overheats (on my laptop, the computer it supposed to operate around 50 degrees C, but when the fan is not working it quickly heads beyond 65C and shuts off around 100C).

One trick that may work for you is to unplug the laptop, just for a few seconds, after it has resumed from hibernate. On my laptop, this triggers the fan and the computer no longer runs the danger of overheating. Without this trick, I would never use hibernate because of the danger to the computer.

---

