---
title: "No video plays after hibernation"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by spupy on 2007-07-25
After reading some threads about hibernation,  i got it working with this command as root:
```
echo -n "disk" > /sys/power/state
```

Everything is working fine except:
1. The double console switch option in a config file i cant remember doesnt work - i still have to switch away and back to X manually. But that is no pain for me.

2. The real problem is that after resume from hibernation mplayer and totem wont play any video -no picture, only sound. I use mplayer -vo xv. With video output x11 it works but the quality is bad and cant go fullscreen.

Im kinda noob about such things, but i suspect the fglrx driver is the culprit (wow what a detective huh :/). Is there anyway to "restart" the video?:confused:

Thank you in advance!

---

### Post by spupy on 2007-07-27
Ok,  the solution to the video problem is a restart of X. Now about that hibernation config file... bump!

---

