---
title: "Issue with high CPU usage of Xorg and issue after switching graphics card"
date: 2018-03-05
forum: Hardware
---

### Post by henrik-andersson on 2018-03-05
Hey!

I've had two different issues that both have appeared after I switched from an dedicated graphics card to the internal built-in gfx card (Matrox Electronics Systems Ltd. MGA G200e [Pilot] ServerEngines (SEP1) (rev 02)).

The first issue I have is that Xorg takes up alot (between 80-100% of the CPU) all the time.
It doesn't matter if I'm doing anything special or not, everything else can be idle but Xorg still uses alot of CPU.
I have used htop to monitor my processes.
I've read around on the net alot but not really found any direct solution that would fit me.
I use Ubuntu 16.04.4 LTS with Unity as my Window Manager.

If there's anything that you need to be able to mabye help me solve this issue I'm more than willing to supply this information to you.

The second issue is that after I switched my dedicated graphics card to use the built-in instead I was forced to use an VGA cable from the graphics card to the monitor, before I had used an DVI cable.
This is simply because the dedicated gfx card has one DVI port and one HDMI port, and the built-in gfx card has only one VGA port.
So to the real issue, after I switched I got really low resolution on my monitor (BenQ 27") and I have always run 1920x1080 on this monitor.
I started to experiment with xrandr and those things so finally I managed to get the resolution up to my normal resolution, BUT now I see artefacts like you would see if you set too high Hz on a monitor that simply couldn't cope with it.
I can still use the monitor with this resolution with these arcefacts, but it's really irritating for your eyes when you sit for up to 36 hours straight in front of the computer and work.

Could someone please help me with either of these issues I would be VERY happy!

Sincerely Yours
Henrik 'DesTr0yeR' Andersson

---

### Post by Yellow Pasque on 2018-03-06
Start here:
```
glxinfo -B
```

IIRC, Matrox doesn't do 3D hardware accel on Linux. I'm not surprised that running Unity consumes the CPU. I'd strongly recommend a lighter desktop if you continue to use the integrated GPU.
I don't know about the resolution issues, but how much video memory does the G200e use? Maybe this is a clue: 
> At the larger resolutions, the g200e series sometimes struggles with maintaining a proper output. Problems like flickering or black bands appearing on screen can occur.
-- [https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/drivers/gpu/drm/mgag200/mgag200_mode.c?id=abbee6238775c6633a3779962e9e5b5cb9823749](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/drivers/gpu/drm/mgag200/mgag200_mode.c?id=abbee6238775c6633a3779962e9e5b5cb9823749)

In general, the Matrox G200e does not make for a good GPU for daily use. I would recommend another card.

---

