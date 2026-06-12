---
title: "Gamecon and NES pad"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by BBin on 2007-10-28
I googled a bit and found out about gamecon, it is supposed to be able to handle both NES and SNES gamepads, but I can't find what configuration to use for NES pads anywhere, only SNES.

For snes it is:
#!/bin/sh
modprobe -r lp
modprobe gamecon map=0,1,0,0,0,0
modprobe gamecon gc=0,1

I tried it and it says button 0, 2, 4 and 5 is on all the time (using jstest, the rest of the buttons and the up, down, let and right are working) and I can't configure any emulator, when I try it says button 5 was pressed every time.

Any ideas?
//Robin

---

