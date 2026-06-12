---
title: "Install Nvidia GeForce GT555M drivers in Ubuntu 12.04"
date: 2012-07-07
forum: Hardware
---

### Post by Rhemat on 2012-07-07
Heya All,

I just installed Ubuntu 12.04 on a laptop I got yesterday (Asus N75S), which comes with an nVidia GeForce GT555M video processor.  However, it appears that the video drivers were not properly installed, as I get errors like this when trying to play games:

```

GLimp_Init() - could not load OpenGL subsystem. See "/home/user/.openarena/baseoa/crashlog.txt" for details.

```

```

Xlib:  extension "GLX" missing on display ":0.0".

```

I've installed mesa-utils, and tried reinstalling nvidia-current, but nothing works.  Is there another package I need?

Thanks in advance.

---

### Post by Perfect Storm on 2012-07-07
Have you tried through the 'additional Driver' app instead?

---

### Post by Rhemat on 2012-07-07
At first, there were no additional drivers.  Then after trying to follow some guides online, something changed, and displayed 2 nVidia drivers "nvidia-current," and "nvidia-current-update."  Both of those drivers put my display into a 640x480 resolution, the nVidia settings manager said that I wasn't using nVidia drivers, and wouldn't let me change the resolution to anything higher.  I tried the Settings Manager > Display, and 640x480 was max resolution there too.  I managed to make a backup configuration file for xorg earlier, so I was able to get a more usable display back.

I get glxgears, but the output is abysmal for the prowess of the processor (60FPS).

---

### Post by efflandt on 2012-07-07
When you have "Sync to vblank" enabled in nvidia settings it is normal for glxgears to run at the refresh rate of your display 60 Hz (fps).  If I disable that on a desktop GTX 550 Ti it goes up to around 3600-3700+ fps in a window or 129 fps 1080p full screen.

But if NVIDIA X Server Settings does not work properly you might not be able to do anything about that.  What guides did you follow?

What does **dpkg-query -l nvidia*** show for nvidia-current version?

What modules show in output of **sudo lspci -v** for your video which would typically be:
Kernel driver in use: nvidia
Kernel modules: nvidia_current, nouveau, nvidiafb

Have you tried adding x-swat to your repositories to try nvidia 302.17 or was that how you got something to show up in Additional Drivers?

---

### Post by Rhemat on 2012-07-07
Okay, just installed nvidia-current, and here is the output to your questions:

dpkg-query -l nvidia*
```

302.17-0ubuntu1~precise~xup

```

lspci -v
```

VGA compatible controller: NVIDIA Corporation GF106 [GeForce GT 555M] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 2051
	Flags: fast devsel, IRQ 11
	Memory at da000000 (32-bit, non-prefetchable) [disabled] [size=32M]
	Memory at c0000000 (64-bit, prefetchable) [disabled] [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [disabled] [size=64M]
	I/O ports at d000 [disabled] [size=128]
	Expansion ROM at dc000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information: Len=14 <?>
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel modules: nvidia_current, nouveau, nvidiafb

```

I have added x-swat to my repositories, and installed the nVidia drivers.  Currently, my display is fine, but still no 3D acceleration, I get the following error from OpenArena again (first error output from first post).  Compiz has stopped working (screen zoom), so I'm going to uninstall the nVidia drivers.

I've tried using the Additional Drivers solution, I've tried the nouveau drivers (that is what gave me the glxgears output), I've tried adding the ppa:x-swat solution.

---

### Post by Rhemat on 2012-07-10
I found out that the laptop I have uses nVidia Optimus technology, and I've read that the Linux Drivers do not do well with Optimus.  Am I better off just returning the laptop, or are there some things I could try that would provide a decent solution?

---

### Post by ELD on 2012-07-10
You can try The Bumblebee Project but that's not 100%, it only works with certain types of Optimus.

---

### Post by Rhemat on 2012-07-10
I did try it, and it is working.

My only problem, and I don't know what is causing it, is that I can't seem to set games to play widescreen, at least properly:

TuxGames will just play 4:3, even when I tell it 1920x1080.
Quake3 will use an extremely wide resolution/aspect ratio (like 3:1), even though I set it as follows:

```

seta r_customwidth "1920"
seta r_customheight "1080"
seta r_mode "-1"

```

Also, when the games exit, they return me at a resolution of 640x480.

Thanks again for your help.

---

### Post by Rhemat on 2012-07-10
I just uninstalled Bumblebee, and tried IronHide.  It provides a bit better performance, for me at least.  Unfortunately, I don't think it even uses 80% of what the GPU is capable of, but given the circumstances, I can understand why.

Plus, it doesn't lower the resolution after I get done playing a game, so that is a definite plus.

I hope that nVidia does create Linux Optimus technology drivers soon, because I really want to take advantage of this laptop.  My old laptop does very well with games, but it can still stutter at times (especially with MineCraft, but I think that is a JAVA thing).

Thanks again for your assistance.

---

