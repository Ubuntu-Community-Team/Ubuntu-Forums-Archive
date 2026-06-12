---
title: "[SOLVED] Troubleshooting hdaps (hard disk protection) on Thinkpad T61"
date: 2008-08-23
forum: General Help
---

### Post by sancho panza on 2008-08-23
I'm not able to get any response from the accelerometer/hpaps.
I have installed hpapsd and hpaps-utils from the repos. The command 
```
sudo modprobe hpaps
``` loads the module without fuss. But the commands hpaps-gl and hpaps-pivot indicate  no movement when I move/tilt laptop.

I'm aware that hard-disk parking is buggy and I'm not worrying about it right now. I'm just trying to get a response from hpapsd for now.

---

### Post by sancho panza on 2008-08-23
Fixed it. The package hpapsd from the repos is not needed. The system needs the module hpaps_ec to be loaded. More [instructions here]("http://socallinux.org/pipermail/linuxusers/2008-May/003555.html"). Make sure the module hpapsd or tp_smapi are unloaded using *sudo modprobe -v hpapsd* or sudo *modprobe -v tp_smapi* before loading hpaps_ec.

Then, hpaps-gl and hpaps-pivot from the package hpaps-utils work as expected.

---

### Post by feeshy on 2008-08-26
Thanks for this, worked perfectly on my T61.  And playing Neverball with the accelerometer is cool (in a geeky sort of way).

---

### Post by sancho panza on 2008-08-26
Hey, but I'm unable to tweak the sensitivity of the accelerometers for neverball. Without it, its not much fun, as the ball/table moves way slower than one would expect in reality. The ball/table moves much faster with the touchpad.

Let me know if you have figured that out.

---

