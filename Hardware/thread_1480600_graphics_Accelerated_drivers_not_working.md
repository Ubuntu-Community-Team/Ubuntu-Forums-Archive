---
title: "graphics Accelerated drivers not working"
date: 2010-05-11
forum: Hardware
---

### Post by razwiss on 2010-05-11
Hi,

Installed Ubuntu 10.04  64 bits on a Sony Vaio laptop VPCF111FD with a nvidia Geforce 310M graphic card. With Cuda.

Everything seemed to work fine until I tried to enable visual effects and games, says I must install the third party video drivers from System -> Administration -> Hardware driver.

So I did it, installed the third party nvidia graphics accelerated 2D-3D drivers.

When I restarted the computer ,as asked for, there was major artifacts on the top of the screen (multi-colored lines and tearing), and the screen was split on the median: left part was on the right and right on the left.

From what I was able to read (not exactly but quite the same):

Nvidia failed to load for the following reason: the Nvidia module couldn't find any screen to work to.

After clicking OK there was 4 options : start in failsafe, troubleshoot, solve the issue in command line, and restart I think.

Followed multiple guides on internet for installing nvidia's site drivers. Encountered the malicious "nvidia.ko" error. Solved it. Says it has successfully installed but when I start X the screen turns black. It seems to be the screen since i type and I can see the processing LED on the laptop blinking.

I plugged an external display but I can't get a picture on it.

Any idea on how to solve this ? Thanks

---

### Post by razwiss on 2010-05-11
Bumpity Bump

---

### Post by razwiss on 2010-05-12
rebump.

Anyone has an idea ? I really like ubuntu, it's perfect for my laptop. Plus, it extended my battery life by 2 fold. I would really appreciate if this could be solved.


I'm a computer science graduate so I don't have any difficulties understanding anything, nor using console commands.

---

### Post by razwiss on 2010-05-12
Another desperate bump

---

### Post by Slayer6 on 2010-05-14
I am having the exact same problem with a VAIO VPCCW21FX  NVIDIA 310m.  I've tried enabling hardware drivers, installing newest and one back versions from NVIDIA's site.  No luck.  Finally got through the screen blacking out totally with nomodeset and now this.  Well, I can go on using low-res generic driver but really would like to get this solved.  For now I'm stuck working in windows 7 most of the time.  This doesn't seem to be so much of a setting issue but a real incompatibility.  Anyone that does have this working pls pls let me know what ya did

---

### Post by razwiss on 2010-05-14
Hi Slayer6,

Fortunately for you, your CCW series laptop can be solved ! :popcorn:

here's the thread: [http://ubuntuforums.org/showthread.php?t=1392766&highlight=310m](http://ubuntuforums.org/showthread.php?t=1392766&highlight=310m)


The EDID method will get you a picture after the driver install.


As for my laptop (F series late 2009), EDID doesn't work. Tried with both softmccs and phoenix EDID, both can't get it.

Sounds like nothing will work until nvidia's update. Or is it an EDID software under linux that might work ?

---

