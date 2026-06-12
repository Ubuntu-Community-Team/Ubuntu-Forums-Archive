---
title: "need help with compiz / video card driver ubuntu 8.04"
date: 2008-09-07
forum: General Help
---

### Post by omnispyder on 2008-09-07
Hello I have a hp dv9634ca notebook. 8.04 works great video sound.
But my video card is not working properly. Im trying to get compiz to work but nothing happens. Any idea how I can install my drivers.

when i goto my hardware drivers in applications, nothing shows up.

this is my hardware specs

Driver - Audio Date Version
» Realtek High-Definition Audio Driver
03-2008 6.0.1.5548 A

Driver - Graphics Date Version
» Mobile Intel 965 Express Chipset Family Video Driver
03-2008 7.14.10.1437 A
» NVIDIA GeForce Series Video Driver
03-2008 7.15.11.7432 A

If anyone can help me install thses drivers and get compiz working id greatly appreciate it.

---

### Post by terrax on 2008-09-07
Uhmm you got both an intel and a nvidia gfx card?

Try write this in the terminal:

```

lspci

```

Please paste the output here.

If you got a nvidia card. Just install envyng-gtk (gnome) or envyng-qt (kde).

Then you can find envy in the gnome menu under system.

---

