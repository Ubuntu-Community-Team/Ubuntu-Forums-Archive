---
title: "Kubuntu 8.04 (64 bit) does not detect my Sidewinder Gamepad"
date: 2008-08-08
forum: Hardware
---

### Post by brandonblm on 2008-08-08
I have a Sidewinder Gamepad. I can't get my Kubutnu 8.04 (64) system to detect it. I have tried every thread and post and followed all instructions. but it simply will not find my device. I was on the IRC chat and a gentleman was trying to help me by having me pastedbin several files. But, he then had to go and was not able to help me further. Can someone walk me through this as I am a Noob. 

Thanks,
Brandon

---

### Post by dagoss on 2008-09-08
I'm also having trouble with this.  Oddly, when I originally used Ubunutu 8.04, the gamepad was detected automatically.

EDIT:

Try this,

run ls mod and look for "gameport".  If that isn't there, you'll need to figure out what the correct module is for your sound card's gameport.

Then modprobe joydev and sidewinder.  For my system, I added these lines to /etc/modules:
```

emu10k1-gp
joydev
sidewinder

```

---

