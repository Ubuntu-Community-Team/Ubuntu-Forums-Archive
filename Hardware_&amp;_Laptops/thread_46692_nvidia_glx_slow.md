---
title: "nvidia glx slow"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by pumaman_scotland on 2005-07-05
Hi,

I am running Hoary, and am having a slight problem with my nVidia 3D graphics acceleration, and I wonder if you have any ideas:

Problem - I am getting *very* low performance - glxgears only gives me 8.800 FPS! This makes games suck.

The nvidia drivers are installed correctly:
  [list]I installed the nvidia-glx & nvidia-settings packages, and ran nvidia-glx-config enable.[/list]
  [list]I get the nvidia splash when X starts[/list]
  [list]xorg.conf contains nvidia & glx instead of nv & dri[/list]
  [list]x.org logs show that nvidia driver is loaded fine[/list]
  [list]glxinfo includes the lines:[/list]
        ```
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 MX 440 with AGP8X/AGP/SSE/3DNOW!
OpenGL version string: 1.5.3 NVIDIA 71.7
```4

So, as far as I can tell, it should be working!
If you have any ideas what could be wrong, please let me know.

thanks
David

---

### Post by netrattler on 2005-07-05
I'll check mine out I have the same card and see what I get.

Joe

---

### Post by neurosion on 2005-07-06
Is that 8800 or literally 8 FPS and change?

If you mean 8800 FPS, you may be maxed out.  I get somewhere in the 11000 FPS range with a 6800GT Ultra, and a 2500 FPS differential seems just about right.

If you mean 8 FPS, then post the results of "dmesg | grep agp" and "lsmod | grep agp" so we can see if AGP is working correctly.

---

### Post by pumaman_scotland on 2005-07-06
No, I literaly mean 8FPS.

However, when I ran glxgears today, I got a far more respectable 1230 FPS.
I still don't know what was wrong yesterday. If it happens again I'll check my dmesg & lsmod, but thanks for taking an interest.

```
pumaman@hal:~ $ dmesg | grep agp
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected NVIDIA nForce2 chipset
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: AGP aperture is 64M @ 0xe0000000
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
pumaman@hal:~ $ lsmod | grep agp
nvidia_agp              7452  1
agpgart                31784  2 nvidia_agp,nvidia
```

---

### Post by neurosion on 2005-07-06
Your AGP settings look fine, so I'm not sure where to take you from here.  Maybe 1250 is the best that card can do on Linux.  Glad to see the 8.8 was an anomaly.

---

### Post by wylfing on 2005-07-06
I am not too knowledgeable about how the Ubuntu-packaged drivers are built (I always "roll my own" from the nVidia web site). However, you should try blacklisting nvidia_agp. It's almost certainly preventing the native nVidia GART from functioning, thereby killing your OpenGL performance.

Try this:
1. Switch to a console by pressing Ctrl+Alt+F1.
2. Log in.
3. Type 'sudo killall gdm' to stop X.
4. Type 'sudo pico /etc/hotplug/blacklist'.
5. Arrow down to the bottom of the file and type 'nvidia_agp' on its own line (no quotes).
6. Save the file with Ctrl+W and exit with Ctrl+X. (I'm going from memory -- you'll see the commands at the bottom of the screen, just remember that ^ means Ctrl).

Now unload all the modules:
7. Type 'sudo rmmod -f nvidia'.
8. Type 'sudo rmmod -f nvidia_agp'.
9. Type 'sudo rmmod -f agpgart'.

Now load nvidia back in:
10. Type 'sudo modprobe nvidia'. (This will automagically load agpgart too, but not nvidia_agp.)

Restart X:
11. Type 'sudo /etc/init.d/gdm restart'.

Last but not least, try glxgears again and see if your performance is better.

---

