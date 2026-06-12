---
title: "Help configure my monitor"
date: 2010-09-01
forum: Hardware
---

### Post by madap on 2010-09-01
My monitor hasn't been properly detected by X when I installed Ubuntu 10.04 today.
The native resolution of this 22" Asus VW223B is 1680x1050, it's not offered in either the change resolution app, or xrandr

My xorg.conf is really vague:
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

```I've been through some tutorials and forum posts but it's quite confusing as to what I have to do to get this working... 
Cheers in advance

---

### Post by madap on 2010-09-19
Sooo new symptom... 
Took a photo cos you can't screenshot the booting screens, obviously xD

[IMG]http://i53.tinypic.com/118m5cp.jpg[/IMG]

Obviously my monitor is screwed up somehow, even when I update the ATi drivers in Windows, the next reboot my whole screen is stretched (it pans when you near the mouse to the edge of the screens and is set to 1600x1200, which my monitor doesn't support). I have to go into the ATi control panel, disable EDID, and force set it to 1680x1050

So my question here is... is it easy to fix in Ubuntu? Can you 'flash' a monitor's EDID? Is this enough grounds to take the monitor back to the store I bought it from?

Please do reply even if you think your answer couldn't help, it might...

edit: sorry about size, I thought the forum auto-smalled the pics.

---

### Post by madap on 2010-09-28
Weekly bump... Still no answer.:(

---

