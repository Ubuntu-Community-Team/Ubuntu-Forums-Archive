---
title: "Intel &amp; Nvidia Optimus - Won't play nice..."
date: 2014-06-04
forum: Hardware
---

### Post by CourtJester140 on 2014-06-04
Hello!
I have an HP Envy 17 laptop that I have installed CAE Linux on, which is just a compilation of open source engineering programs wrapped into one lovely ubuntu package (12.04).

This is pretty much my first meaningful experience with linux, so i'm learning as I go.  I spent a couple of days successfully getting the wifi to work properly.  Now my next task is getting linux to use the nvidia card in this laptop as the dedicated gpu, rather than the i7's graphical processing capability.

I've done a lot of research into this, and from what I've gathered i have an "optimus" setup...an Nvidia 740M paired with an intel i7, where the nvidia card is only meant to take over as the gpu when the system calls for it.  I've also attempted a lot of different methods to try to get the nvidia card to come to life as my primary GPU.  Unfortunately i've been completely unsuccesful, and have made zero progress, tried tools like bumblebee, and even just went the straight driver route.

So, can anyone help me to get my nvidia card to work properly?  I am not sure what sort of terminal outputs you guys will want to see, but here's one that i think tells a lot...

lspci -v

```
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 1966
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at d3000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 7000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>



01:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)
    Subsystem: Hewlett-Packard Company Device 1966
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 6000 [size=128]
    Expansion ROM at b2000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_331_updates, nouveau, nvidiafb
```

Let me know if there is anything else you want to see.
Thank you!

---

### Post by mastablasta on 2014-06-05
> **CourtJester140 said:**
> 
I've done a lot of research into this, and from what I've gathered i have an "optimus" setup...an Nvidia 740M paired with an intel i7, where the nvidia card is only meant to take over as the gpu when the system calls for it.  I've also attempted a lot of different methods to try to get the nvidia card to come to life as my primary GPU.  Unfortunately i've been completely unsuccesful, and have made zero progress, tried tools like bumblebee, and even just went the straight driver route.



what does "zero progress" mean? surely if it didn't work there were some error messages?!? you do need to use bumblebee to get it working since nVidia does not support Optimus under Linux.: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

furthermore 12.04 is 2 years old (April 2012) and uses old kernel. it might be good to use newer kernel, newer drivers instead (e.g. 14.04) especially if your computer is from 2012...

---

### Post by CourtJester140 on 2014-06-05
> **mastablasta said:**
> what does "zero progress" mean? surely if it didn't work there were some error messages?!? you do need to use bumblebee to get it working since nVidia does not support Optimus under Linux.: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

furthermore 12.04 is 2 years old (April 2012) and uses old kernel. it might be good to use newer kernel, newer drivers instead (e.g. 14.04) especially if your computer is from 2012...

I quite literally made zero progress.  I attempted a lot of things (unfortunately didn't keep a good record of what I did, lesson learned there), made some progress I thought, but after about a week at this GPU issue i've somehow managed to arrive exactly where I started, which might as well be a clean install.

I'm concerned that I am doing something wrong or missing steps that may be "implied" in some guides (several are written for experienced ubuntu users).  I want to vett as many possibilities as I can before upgrading to a newer version.

---

### Post by CourtJester140 on 2014-06-07
bump!  after a clean install, and digging into the conf file, i noticed that bumblebee.conf was pointing to the wrong directory!! so I fixed that and a double checked that all file paths were correct.  still no luck.  here's a very verbose output...
```

[2430.647867] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 2430.648667] [INFO]Configured driver: nvidia
[ 2430.649065] [DEBUG]optirun version 3.2.1 starting...
[ 2430.649149] [DEBUG]Active configuration:
[ 2430.649201] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 2430.649253] [DEBUG] X display: :8
[ 2430.649296] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-304-updates:/usr/lib32/nvidia-304-updates
[ 2430.649333] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 2430.649374] [DEBUG] Accel/display bridge: auto
[ 2430.649412] [DEBUG] VGL Compression: proxy
[ 2430.649453] [DEBUG] VGLrun extra options: 
[ 2430.649493] [DEBUG] Primus LD Path: /usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
[ 2430.649655] [DEBUG]Using auto-detected bridge virtualgl
[ 2430.768115] [INFO]Response: No - error: Could not load GPU driver

[ 2430.768145] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[ 2430.768163] [DEBUG]Socket closed.
[ 2430.768194] [ERROR]Aborting because fallback start is disabled.
[ 2430.768203] [DEBUG]Killing all remaining processes.

```

---

