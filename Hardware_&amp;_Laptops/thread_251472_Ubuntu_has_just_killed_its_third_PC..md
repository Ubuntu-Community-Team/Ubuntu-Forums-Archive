---
title: "Ubuntu has just killed its third PC."
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by MattKemp on 2006-09-05
I've been having a barrel of laughs lately with Ubuntu killing my graphics cards. Originally it took down my ATi laptop. Then it killed a nVidia 6800. Now it's in the process of killing my new nVidia 7300GS, bought a few weeks ago.

I don't know what it's happening so I've decided to post in here, to see if anyone more friendly with hardware as any idea why it mutilated graphics cards so. About ten minutes ago it ran glxgears for about forty seconds before it froze. My laptop no longer stays up in any kind of GUI, windows or linux. My other graphics card is currently sitting in an anti-static bag.

Someone please explain why an operating system can do this. I can't really afford to buy another one just to make it explode again. I don't want to go back to windows.

---

### Post by crackseller on 2006-09-05
I never really considered posting this because it just sounds "impossible" but, to be honest, since I run Ubuntu my GeForce 6800GT is kinda wracked. The reason is that since I have Ubuntu installed my gfx randomly fails (in Windows, Linux, even during the boot and in the BIOS). Sometimes it would show wonky stuff like missing pixels, sometimes missing lines in the picture and if I play games (be it d3d or opengl) it would show massive render and texture problems, besides that is sometimes won't show anything at all. This is behavour undoublty occured since I use Ubuntu. BUT I would NOT say it is Ubuntu rather than the nvidia driver being responsible for breaking my fgx card, what so ever. I can only speculate about the reason at this point but something definitly broke my card.

//edit: I just saw you said one of your cards was ATI. Sorta rules out my nvidia driver theory then ... :/

---

### Post by OmniDistortion on 2006-09-05
Are you using the same motherboard for all of these cards?

---

### Post by MattKemp on 2006-09-05
> **OmniDistortion said:**
> Are you using the same motherboard for all of these cards?

No. The ATi one was a motherboard card in a laptop, the other two were a 754 and 939 board respectively. The latest card is PCI-E, , in comparison to the old AGP nVidia.

The only thing concurrent between the nVidia cards is the hard drive and memory. This doen't explain the reaction from the laptop, though.

The only thing concurrent between all three PCs is Ubuntu and World of Warcraft. It's not limited to warcraft, however, as I've crashed while running glxgears and a few minutes ago my X reset when using Google Maps. (As a sidenote, glxgears gives me 1500 FPS. i've heard reports on here of 13k+.)

if it helps at all:

```
0000:05:00.0 0300: 10de:01df (rev a1)
```
is given out by lspci -n and

```
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01df (rev a1)
```

from lspci |grep VGA. 

relevant part of xorg.conf:

```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    SubSection     "Display"
        Depth       24
        Modes      "2560x1024" "2048x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "2560x1024" "2048x768"
    EndSubSection
EndSection

```

I can't think of any more relevant output, except that it's damn annoying.

Any help appreciated.

---

