---
title: "Texture Corruption on Nvidia Geforce Quadro"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by EtanSivad on 2007-05-08
I've been getting weird graphical glitches in Ubuntu opengl rendering.  I've been searching forums for the last couple of days, but not making any headway.

I've installed the NvidiaGLXnew drivers, but I still get this: [IMG]http://home.comcast.net/~linasach/Screenshot.png[/IMG]
[IMG]http://home.comcast.net/~linasach/Screenshot-2.png[/IMG]

It's a dell D620 laptop with a Quadro NVS 110M video card.

aka, lspci -n | grep 0300: 01:00.0 0300: 10de:01d7 (rev a1)

And my xorg.confg for good measure:

Section "Device"
    Identifier     "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
   

Any help would be greatly appreciated.

---

### Post by TuneX on 2007-05-11
Same here. Especially big textures cause those rendering glitches to appear very quickly (i.e. the Flip3D screensaver). At first I feared that I might have got faulty hardware but I was neither able to reproduce those glitches on that other operating system nor on Ubuntu Edgy Eft, which comes with an older version of NVidia's commercial driver. As soon as I have the time I will test this specific driver version against Feisty's kernel to see if this is a driver related bug.

Hardware: Dell D620, Intel Core 2 Duo T7200,1GB RAM, Quadro NVS 110M, WXGA+ (1440x900) TFT

---

### Post by TuneX on 2007-05-19
I've started a new thread on the [[COLOR="Blue"]_NVnews forums_[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?t=91641") which are visited regularly by some Nvidia developers. Feel free to add some comments since there are the people who can actually fix that bug.

---

