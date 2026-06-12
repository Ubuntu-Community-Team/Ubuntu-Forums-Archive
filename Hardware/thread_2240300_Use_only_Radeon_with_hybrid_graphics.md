---
title: "Use only Radeon with hybrid graphics"
date: 2014-08-19
forum: Hardware
---

### Post by Graeme_Pietersz on 2014-08-19
I have a laptop that has an issue with overheating that is apparently caused by the GPU. It has hybrid graphics (Intel + Radeon) and as I had it on intel only in the BIOS I assume it is the intel GPU that is causing the problem.

I have change the BIOS settings and have the "radeon" driver installed, which I think means that both GPUs will be used. I am pretty sure the Radeon is muxless but would appreciate confirmation. lspci says it is "Radeon HD 7550M/7570M/7650M"

Is it possible to change the settings so that just the Radeon GPU is used? I do not mind using the properietary drivers if necessary. Even better would be to use Radeon when plugged in and Intel when on battery power - but the main point of it is to see whether using the Radeon makes any difference to the problem. Yes I know that the Radeon will generally run hotter, but being able to swtich between the two may help me isolate the problem.

---

### Post by anchitsingh9 on 2014-08-20
What version of Ubuntu are you using..?

---

### Post by Graeme_Pietersz on 2014-08-21
I knew I had forgotten something pertinant! I am using Trusty.

I also have a problem with a freeze when using fglrx-updates drivers (which I just tried). I do not particularly care which drivers I use (apart from a prefernce for the open source ones).

---

### Post by anchitsingh9 on 2014-08-21
I too had problems with the fglrx-updates, my system went into low graphics mode on restart. The probelm is that fglrx-updates are experimental and therefore it is advised to use the "fglrx" only drivers, they are more stable. Install "fglrx", restart, open AMD Catalyst Control Center(administrative) and choose Intel for power saving and to avoid over-heating.
Anyway let me inform you that since kernel version 3.12, Linux provides "Dynamic Power Management", that is, it turns off the graphics card not in use, when using open-source drivers.

So before experimenting with fglrx, could you post the output for this in terminal :
> sudo cat /sys/kernel/debug/vgaswitcheroo/switch

---

### Post by Graeme_Pietersz on 2014-08-23
I am using the radeon driver, not fglrx, because both fglrx and fglrx-updates cause a freeze on resume from sleep.

```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynOff:0000:01:00.0
```

It is available:

```
xrandr --listproviders
Providers: number : 3
Provider 0: id: 0x6f cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 5 associated providers: 2 name:Intel
Provider 1: id: 0x46 cap: 0x6, Sink Output, Source Offload crtcs: 6 outputs: 1 associated providers: 2 name:radeon
Provider 2: id: 0x46 cap: 0x6, Sink Output, Source Offload crtcs: 6 outputs: 1 associated providers: 2 name:radeon

```

I do not know whether it is even possible to turn off the Intel graphics altogether on  muxless system, but anything that will take load off it may help.

---

### Post by Graeme_Pietersz on 2014-08-23
I think the problem may be with the fan or fan control, not the amount of heat produced so I have started a new thread asking about that.

---

### Post by anchitsingh9 on 2014-08-23
> sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+ Pwr:0000:00:02.0
1DIS: DynOff:0000:01:00.0

The discrete graphics is off.
What about the battery backup..?

---

### Post by Graeme_Pietersz on 2014-08-23
Thanks, so its not even on! I can get it on DynPwr for a while by logging out, using vgaswitcheroo, then restarting lightdm. It goes back to DynOff after a few minutes.

What do I do about it?

> What about the battery backup..?                 

What battery backup

---

### Post by anchitsingh9 on 2014-08-24
If you want to avoid overheating, why do you want to turn on the discrete GPU in the firstplace.
If you run your system on discrete GPU only, the fans will run like hell.
In Windows OS, the rendering is done using the Discrete GPU, while the integrated one is used for display. The driver in windows handles it, therefore avoiding any overheating and giving better running time on the battery.
In linux, Xorg does not support the auto switching of GPUs presently. You can check it here:
[https://wiki.archlinux.org/index.php/hybrid_graphics#Current_Problems_2](https://wiki.archlinux.org/index.php/hybrid_graphics#Current_Problems_2)

> What battery backup

By battery backup I meant, what is the running time of your laptop on batteries..? Is it normal or do you think otherwise..?
Maybe the dynamic power management feature is not working properly, or there is a bug in the open-source intel/ati driver.(this is not specific to your system)

---

### Post by Graeme_Pietersz on 2014-08-24
This also look weird to me:

```
glxinfo |grep renderer
libGL error: failed to open drm device: Permission denied
libGL error: failed to load driver: i965
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer,
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
```

but

```
sudo glxinfo |grep renderer
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer,
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer,
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile
```

reproducible.

---

### Post by Graeme_Pietersz on 2014-08-25
I reinstalled the intel drivers and glxinfo now consistently showing ivybridge mobile, but its perceptibly hot AND radeon is still always DynOff even when playing a graphics heavy game (0AD).

---

### Post by anchitsingh9 on 2014-08-25
Yes, this is how it works right now.
Like I told you dynamic switching doesn't work currently.
Also you should check this :

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1304912](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1304912)

---

### Post by Graeme_Pietersz on 2014-08-26
Thanks for the link to that bug - it could well be the problem, except that I have radeon graphics off in the BIOS.

---

