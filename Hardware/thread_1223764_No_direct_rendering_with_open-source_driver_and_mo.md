---
title: "No direct rendering with open-source driver and mobile FireGL v5200"
date: 2009-07-26
forum: Hardware
---

### Post by zak on 2009-07-26
When I first upgraded to 9.04, this worked fine. For a while, I had switched to custom Xserver 1.5 packages and fglrx, but at the moment I want to switch back to the open source Radeon driver.

I ran a dist-upgrade last night and I'm back to the latest Jaunty packages for... everything. No matter what I do, I get no acceleration.

[Xorg log](http://paste.ubuntu.com/234021/)
[xorg.conf](http://paste.ubuntu.com/234024/)

```

zak@shinybox:~$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0bff00000 ( 3071MB), size=    1MB, count=1: uncachable
zak@shinybox:~$ dmesg|grep mtrr
[  427.018273] mtrr: no MTRR for d0000000,10000000 found

```

---

### Post by zak on 2009-07-27
Solved: nvidia-glx-96 is installed by default to provide libGLcore, but it also diverts libglx, and xorg-video-radeon needs the Mesa version. Reinstalling libgl1-mesa-glx after nvidia-glx-96 is installed solved the problem.

Now if I could just figure out why enabling compositing draws almost everything upside-down....

---

