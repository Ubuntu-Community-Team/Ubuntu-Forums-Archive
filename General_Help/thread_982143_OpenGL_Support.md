---
title: "OpenGL Support"
date: 2008-11-14
forum: General Help
---

### Post by davidbilla on 2008-11-14
Redirect me to the appropriate place if this has already been posted.

How do I find out whether my video hardware supports OpenGL? I have installed Hardy in an external hard drive and sometimes I have to boot it from certain systems which don't have any separate graphics cards apart from what their motherboards offer by way of on-board graphics support. Two systems are what I mostly try to use, one of which has an 845G Chipset Motherboard and the other has a D946GZ Intel chipset motherboard. I have to use Celestia/Stellarium which require OpenGL support.

Is it absolutely necessary to have a proprietary video card like Nvidia or ATI for OpenGL support to be enabled? Or is there any other way to run Stellarium/Celestia (and if possible, enable desktop effects) on such computers that bypasses the use of a separate graphics card? I'd like to have a coherent picture of things atleast.

Thanks.

---

### Post by CatKiller on 2008-11-14
Pretty much all graphics adaptors from the last decade can accelerate OpenGL to some extent. Some of them are better at it than others, and whether your graphics adaptor will accelerate OpenGL or not depends on the driver that you are using.

The implementation of OpenGL that Ubuntu uses (Mesa 3D) will fall back to just using software rendering if the driver that you are using doesn't accelerate it in hardware. So you'll always have OpenGL support - it just might not be very fast.

I don't know about those two in particular, but the open-source Intel drivers will give reasonable, but not spectacular, OpenGL performance on fairly modern Intel graphics adaptors.

```
glxinfo | grep render
```

will tell you if your OpenGL is hardware-accelerated or not. If it returns "direct rendering: Yes" then you're using hardware acceleration.

---

### Post by davidbilla on 2008-11-15
Thanks for the reply. This is the output I got for "glxinfo | grep render".

```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```


And this is my xorg.conf currently in use:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

There is no 'Driver' under the "Section Device". If I connect it to my other system which has an nvidia card, it says 'Driver Nvidia'. Any idea how I can go about enabling graphics acceleration in the other systems?

Thanks again for your reply.

---

### Post by CatKiller on 2008-11-15
> **davidbilla said:**
> Any idea how I can go about enabling graphics acceleration in the other systems?

Not really, no. Both computers I've used with Intel graphics, acceleration just worked. The computer with NVidia graphics was configured the hard way, before the abstraction away from X that's used by the new graphical setup tools.

But without the GLX extension running, you won't get accelerated graphics.

---

### Post by SamNSane on 2008-11-15
> There is no 'Driver' under the "Section Device". If I connect it to my other system which has an nvidia card, it says 'Driver Nvidia'. Any idea how I can go about enabling graphics acceleration in the other systems?


There being no driver listed on an Intel graphics system is, in my experience, correct. None of mine show a driver since there is no choice between Open Source and restricted for them. Intel video drivers for Linux are all Open Source (AFAIK).

All of my Intel systems, however, give quite a different response to "glxinfo | grep render", for instance the little Panasonic subnotebook tells me:

> 
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel (R) 852GM/855GM 20061017 x86/MMX/SSE2


The reason I'm posting is to caution you about nVidia. Although it appears that the particular Intel system you tested with the command doesn't support OpenGL, you shouldn't assume that you'll get great support from a given nVidia card until you've done pretty thorough research. Bad OpenGL support can be worse than none at all, as many nVidia users today will ruefully tell you.

I've got a Quadro FX Go1400 graphics workstation card that was designed to do OpenGL on one of my systems. The Panasonic's Intel video beats beats it, performance-wise and function-wise, regardless of which restricted or proprietary driver from nVidia I use on the vastly more expensive nVidia card.

I just thought I should mention this before you go plunking down money for nVidia.

nVidia's choice to keep to their proprietary business model for drivers has hampered efforts by the Linux community to make their hardware work on the platform. If I use the Open Source drivers that Ubuntu installs by default on this card, it's behaviors (except for rendering and special effects) are much better. For instance, it can tell which monitor on a notebook I want to use by whether or not I have the notebook docked and the lid open or closed. That feature doesn't work with any of the proprietary drivers. I have to leave the lid open and use Fn-F8 to get to the external monitor.

I also see more freezes and glitches in graphical elements of the OS on the system with the nVidia card.

If my experience were unusual, I'd keep my trap shut. But if you wander over to the nvnews forums or look around on the Ubuntu forums you'll see enough evidence of nVidia's abject failures. There was at one time a kind of love affair between Linux and nVidia because they were at least developing drivers for the platform. But they haven't kept up, and probably can't keep up, because of the lack of intimate involvement that would be needed for their driver developers to integrate their product with Linux.

[http://www.nvnews.net/vbulletin/showthread.php?t=115724]("http://www.nvnews.net/vbulletin/showthread.php?t=115724")

That thread at nvnews contains a few user perspectives and a little information about specific nVidia cards you might want want to avoid.

Someone who knows more about the nitty-gritty of this might be able to suggest a method of getting OpenGL support on your particular systems. If I understood correctly, you're using a portable hard drive and switching it around among systems. I don't know whether or not particular configuration options made to that image could be defeating you. Maybe you need to actually install Ubuntu with the hard drive in place on the system(s) you wish to have supported?

Good luck!

---

### Post by davidbilla on 2008-11-18
> I just thought I should mention this before you go plunking down money for nVidia.

No way. The reason I mentioned a system with an nvidia is that I happen to have one already!

> 
Maybe you need to actually install Ubuntu with the hard drive in place on the system(s) you wish to have supported?

Maybe... I'll let you know if/when I stumble upon anything.

---

### Post by SamNSane on 2008-11-18
> **davidbilla said:**
> No way. The reason I mentioned a system with an nvidia is that I happen to have one already!

That's cool. It only costs you a wee bit of time then.

> Maybe... I'll let you know if/when I stumble upon anything.

I'd appreciate that. I finally got some basic functionality to work along with accelerated OpenGL support on one Quadro-equipped laptop -- functionality that should have just worked (and did work with the Open Source driver). But it cost me a fair amount of spare time over a period of a few weeks to do it. So I'm feeling slightly -- and I do mean slightly -- more kindly disposed toward nVidia right now.

---

