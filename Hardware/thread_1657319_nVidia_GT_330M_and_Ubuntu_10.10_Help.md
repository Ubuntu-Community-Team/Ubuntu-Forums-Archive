---
title: "nVidia GT 330M and Ubuntu 10.10 Help"
date: 2011-01-01
forum: Hardware
---

### Post by ryankask on 2011-01-01
Hi everyone and happy new year! :razz:

My laptop has two graphics cards. According to the relevant lspci output:

```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)

```

I want to use the nVidia card instead of the Intel i915 driver for the Intel graphics card so I can use Compiz.

I've installed **nvidia-current**. Here are the steps I've so far taken:

1. sudo apt-get install nvidia-current - went fine

2. sudo nvidia-xconfig

if I rebooted at this point I get the following errors in my X.org log file:

```

[    24.613] (II) LoadModule: "nvidia"
[    24.613] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    24.614] (II) Module nvidia: vendor="NVIDIA Corporation"
[    24.614] 	compiled for 4.0.2, module version = 1.0.0
[    24.614] 	Module class: X.Org Video Driver
[    24.614] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    24.614] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    24.614] (--) using VT number 8

[    24.620] (EE) No devices detected.
[    24.620] 
Fatal server error:
[    24.620] no screens found
[    24.620] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    24.620] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    24.620] 

```

3. I then added the following line to my X.org configuration's "Device" section:

```
BusID          "PCI:1:0:0"
```

At this point **I've gotten the closest I've ever gotten to successfully setting up the nVidia card**. If I boot up, I can hear the GDM "Coconut shaking" sound that plays on startup **but the cursor "_" just stays there and the screen stays black (not blank)** -- it still shows the "Loading this program.... OK" lines. I'm not sure if the the nVidia card is loading but the nvidia-xconfig generated xorg.conf is in /etc/X11.

If I kill X and use

```
startx
```

I again hear the loading sounds but X doesn't seem to be starting on my screen.

If anyone could help, it would be greatly appreciated!

Below are some links that might be helpful:


[LIST]
[*][My modified nvidia-xconfig xorg.conf file]("http://www2.ryankaskel.com/misc/ubuntu/Xorg.0.log")
[*][The X.org log file I think is successfully loading nvidia]("http://www2.ryankaskel.com/misc/ubuntu/Xorg.0.log")
[*][The "No screens found" X.org log]("http://www2.ryankaskel.com/misc/ubuntu/Xorg.1.log")
[/LIST]


Any help is greatly appreciated!

Best,
Ryan

---

### Post by cascade9 on 2011-01-01
nVidia doesnt support switchable graphics/'optimus' with linux. 

If you dont have a BIOS setting to force the GT330M, or disable the Intel graphics, AFAIK you cant install the nvidia drivers.

---

### Post by ryankask on 2011-01-01
Okay thank you for your quick reply. A few points:

[LIST]
[*]I only want to use the nVidia card and NOT the Intel one
[*]Is there not a way to prevent the Intel card from being read by the kernel?
[*]Is it possible to **use compiz/glx/3d with the Intel i915 driver**
[/LIST]

Thanks very much.

Ryan

---

### Post by realzippy on 2011-01-01
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

---

### Post by ryankask on 2011-01-01
Thanks for the link!

The thing is -- I don't want to use **both cards**.

My goal is to get glx on my machine... so I need to do either of the following:

[LIST=1]
[*]Blacklist the Intel card and use the nvidia card - (note: I've seen some links to blacklisting the Intel card from the Linux Hybrid Graphics page but they 404)
[*]Use the i915 driver with glx -- **Is glx possible with the i915 driver?**
[/LIST]

Thanks,
Ryan

---

### Post by realzippy on 2011-01-01
> **ryankask said:**
> Thanks for the link!

The thing is -- I don't want to use **both cards**.

My goal is to get glx on my machine... so I need to do either of the following:

[LIST=1]
[*]Blacklist the Intel card and use the nvidia card - (note: I've seen some links to blacklisting the Intel card from the Linux Hybrid Graphics page but they 404)
[*]Use the i915 driver with glx -- **Is glx possible with the i915 driver?**
[/LIST]

Thanks,
Ryan

The problem is:
You cannot use both cards,
but both cards are running (and power sucking,especially the nvidia)
The nvidia card cannot address the display (this is occupied by intel)
[I]Fatal server error:
[    24.620] no screens found
[/I]
So the nvidia-current driver does not work.
There is no way "blacklisting" the intel card and get the nvidia driver working,unless you have a BIOS switch.Sony/Alienware laptop/ kernel hacks seem to work sometimes disabling the nvidia-card.

GLX should run out of the box with the intel card;
```
glxinfo | grep direct
```
...have to admit being impressed about compiz running "smoothly" here.

---

### Post by ryankask on 2011-01-01
Realzippy:

Thanks so much for addressing my issue. Okay -- so question one is how can I stop the nVidia card from running (or is that not possible without a BIOS switch which I don't seem to have -- Phoenix SecureCore). I would prefer not to disconnect anything since I occasionally use Windows.

The next question is addressing **why glx isn't working out of the box for the Intel card**:

```

$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

This is the output of lsmod:

```

$ lsmod | grep 915
i915                  334267  3 
drm_kms_helper         32836  1 i915
drm                   206230  3 i915,drm_kms_helper
intel_agp              32462  2 i915
i2c_algo_bit            6208  1 i915
video                  22176  1 i915

```

Any help in fixing this would be appreciated.

Thanks,
Ryan

---

### Post by ryankask on 2011-01-01
Okay I've found the error from the log but I'm not sure what it means. I'll do some research in the meantime but again ... any help would be appreciated!!!

```

[  2531.214] (II) LoadModule: "glx"
[  2531.214] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  2531.214] dlopen: /usr/lib/xorg/modules/extensions/libglx.so: undefined symbol: miEmptyData
[  2531.216] (EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so
[  2531.218] (II) UnloadModule: "glx"
[  2531.218] (EE) Failed to load module "glx" (loader failed, 7)
```

Thanks,
Ryan

---

### Post by ryankask on 2011-01-01
I've been able to fix the glx issues with the i915 card by installing the X.org edgers PPA so obviously the issue has been addressed upstream.

I will mark this as solved even though the original issue isn't as compiz is working beautifully. As realzippy mentioned, the underlying issue of having the nVidia and on-board graphics cards is being addressed.

Thanks.

---

### Post by iammeagain on 2011-05-01
How did you go about installing the X.org edgers PPA? I wanted to see if that would fix my problem, I can't get opengl working after disabling my Nvidia on my xps 15.
Nevermind, sold my issue through this: 
sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

---

### Post by Dmitko on 2011-08-30
Hi,

I've got the same problem with my new Dell Inspiron 5110, with an integrated in the CPU intel adapter and an external NVIDIA GF GT 525 (1GB).

I've reached the point where I see the blank screen and 'hear the coconuts'. I suppose that if I plug an external monitor to the laptop I'll see gnome there. Of course I'd like to use the powerfull GPU in my laptop display. 
Is there realy no way to make the powerful GPU run on the laptop screen?

---

