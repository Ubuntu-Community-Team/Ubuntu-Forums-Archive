---
title: "fglrx driver gone after normal software update"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by kiwited on 2009-07-02
Ubuntu 8.04 LTS, AMD64.

This morning I carried out a software update. The new packages from memory included an updated kernel, although the number was the same as before, I think. Also was an update to fglrx.

After the update I restarted the machine and got a low resolution login screen, and my user screen was also low resolution. I ran the command to reconfigure xorg.conf, which gave a better, but 'stretched' resolution. Under hardware drivers, fglrx is not to be seen, 3D doesn't work any more and my screen resolution is very poor, but useable.

How do I fix this?

Theo

---

### Post by Sidewinder1 on 2009-07-03
I can't answer your question but for future reference, whenever I see a kernel update I search this forum (as I'm doing right now) for "kernel update" to ascertain if anyone with similar configurations to mine is experiencing problems, prior to me hitting the update button. It's no guarantee but adds a little to my peace of mind.

Side

At least this'll act as a shameless bump :-)

---

### Post by kiwited on 2009-07-03
I fixed the problem by downloading the linux driver from the ATI site and installing it.Doesn't explain why a software update should wipe out your graphics driver, but things are back to normal now.
Theo

---

