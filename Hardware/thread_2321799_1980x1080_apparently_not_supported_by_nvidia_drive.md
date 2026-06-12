---
title: "1980x1080 apparently not supported by nvidia drivers"
date: 2016-04-24
forum: Hardware
---

### Post by fbicknel on 2016-04-24
Installed mythbuntu 16.04 yesterday and have been having fits with nvidia-related things. This host was running mythbuntu 12.04 for several years before I installed this new version.

With the default of nvidia-340 installed, playback (and occasionally simple actions like stretching an xfce window) will cause the system to hang with dancing pixels on the screen.

The screen, btw, is a Samsung TV that can render 1920x1080 60Hz.

Anyway, I got the idea of backreving to 304, which actually does fix the hang issue. (so... yay!) But now when the screensaver blanks or if I turn off the TV, that session is still running but can't be displayed when the TV is turned on again. (I've tried all sorts of keyboard and mouse movements, to no avail.) I can still ssh to the host and even bring up any of the consoles (Ctrl-Alt-F1 , for example), and then killall xfce4-session and it resets that session. 

Unfortunately, the sound is gone with the picture and it seems only a reset manages to get that back.

So I figured instead of older, I would try newer. But 361 and 352 give me no option to set the screen resolution to 1920x1080. Then I found this in the log:[    22.546] (WW) ```
NVIDIA(0): The NVIDIA GeForce 8200 GPU installed in this system is
[    22.546] (WW) NVIDIA(0):     supported through the NVIDIA 340.xx Legacy drivers. Please
[    22.546] (WW) NVIDIA(0):     visit http://www.nvidia.com/object/unix.html for more
[    22.546] (WW) NVIDIA(0):     information.  The 361.42 NVIDIA driver will ignore this
[    22.546] (WW) NVIDIA(0):     GPU.  Continuing probe... 
```

Well, that's sad. I guess they're not going for supporting 8200, huh?

I may be in for a hw upgrade.

---

### Post by fbicknel on 2016-04-25
I have an update:

I managed to find a GT 430 (NVIDIA GF108) card and installed it.

I loaded up the 340 drivers and it seems to be working just fine. I guess the old 8200 chipset (on the motherboard) is passe, now.

This card exhibits some video motion artifacts once in a while: these usually look like horizontal lines around the motion in the video.

But at least the hangs are gone and the 1920x1080 is supported.

Still having some issues with sound. The motherboard supports optical (S/PDIF) which worked very well with my Pioneer audio system. But it seems that something doesn't like audio over HDMI (perhaps the Pioneer), so I've had to directly connect to the TV and use the (ick) TV speakers. Maybe another weekend of trying the myriad combinations might finally yield a solution.

---

