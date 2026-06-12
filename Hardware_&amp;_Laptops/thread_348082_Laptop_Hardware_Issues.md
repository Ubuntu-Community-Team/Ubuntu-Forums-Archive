---
title: "Laptop Hardware Issues"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by breakaway on 2007-01-28
Hello,

I just installed Kubuntu 6.10 and Beryl (fully working, except for some minor hardware issues that I would like fixed):

1. Touchpad. With Kubuntu 6.06, if I moved my finger up and down the right side of my touchpad, it was like rolling the mouse wheel up and down. This feature is broken in 6.10? I would really like to fix this, as it makes it quite difficult to scroll up and down pages / menus etc.

2. Video Card is Misdetected - The laptop has a GeForce Go 6400 with 128MB of memory (TurboCache), but Kubuntu seems to think I have a GeForce 6250? Beryl runs pretty well, but I hope I'm not missing out on any performance due to this.

3. Speedstep - I booted with the power on, and ran 

```
cat /proc/cpuinfo/
```

This reported that the CPU was running at ~1729 mhz (Max speed, it's a 1.73Ghz chip)

So I unplugged it, and ran 

```
cat /proc/cpuinfo/
```

This time, it's running at 800mhz. That's good. So I plugged the power cord back in, and ran the command again. It's still at 800mhz? Shouldn't it go back up to 1729mhz?

Any help appreciated :)

---

