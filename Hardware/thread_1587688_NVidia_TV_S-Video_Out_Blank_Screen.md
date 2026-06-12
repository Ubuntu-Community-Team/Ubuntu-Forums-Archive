---
title: "NVidia TV S-Video Out Blank Screen"
date: 2010-10-04
forum: Hardware
---

### Post by dodle on 2010-10-04
I'm trying to hook up my television to my Ubuntu 10.04 machine via S-Video.  When the TV is the only display connected, the machine starts up and I can see the splash screen, but then it goes blank.  I hear the Ubuntu login music but still no picture.  

If I connect my VGA monitor, all output is directed to it, still nothing on the TV.  I then go into NVidia's XServer settings and try to configure the TV.  The only options it gives me are "Disabled" and "TwinView".  I try to set up "TwinView" but here is the error I get:

> Failed to associate display device 'TV-0' with X screen 0.  TwinView cannot be enabled with this combination of display devices.

I have a feeling that the problem has to do with the resolution or refresh rate, but I am not sure.  Does anyone know what I can try?

**Edit:** Here is my entire xorg.conf:
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

I have also looked over [this thread](http://ubuntuforums.org/showthread.php?t=665704), but have not found a solution.

---

### Post by dodle on 2010-11-07
I think I figured out the problem: The card is not capable of using TwinView.

---

