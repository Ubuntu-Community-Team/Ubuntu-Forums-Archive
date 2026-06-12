---
title: "Graphics Card replacement"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by geezerone on 2009-01-12
Hi

I am looking to change graphics card from Nvidia to ATI and have a few questions:

What is the procedure (my xorg.conf states no specifics just "configured video device", "configured screen" etc under entries for each device)?

Is anything needed changing graphics cards with the same chip manufacturer (ATI or Nvidia)?

What is the procedure should the graphics card die when replacing (like one did for me a year or so ago) without re-installation?

TIA

---

### Post by cariboo on 2009-01-12
You don't need to reinstall when you replace a graphics card. Ubuntu should autodetect the change and on startup use the open source driver. Once at the desktop make sure to do any updates before enabling the restricted driver.

Jim

---

### Post by hangfire on 2009-01-12
> **geezerone said:**
> Hi
What is the procedure should the graphics card die when replacing (like one did for me a year or so ago) without re-installation?


```
sudo dpkg-reconfigure xserver-xorg
```

Choose plain-jane VGA

Shut down and do your h/w swap. Boot up. Again, do:

```
sudo dpkg-reconfigure xserver-xorg
```

Choose your new driver.

PS Tell us how it goes, remember to mark thread as "solved" and thanks.

-HF

---

### Post by geezerone on 2009-01-15
I had already replaced card and booted into safe mode and xserver auto fix. I get a display but have no 3rd party driver in hardware drivers option (system). There is some graphics distortion during bootup/login screen too and can't use compiz anymore.

Any ideas without using envy/manual install?

ATI card replaced with ATI card.

xorg.conf:

```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection
```

---

### Post by geezerone on 2009-01-18
Can anyone help as this is a right royal pita?

I have done dpkg-reconfigure xserver-xorg but this only detects keyboard.

I have no proprietary hardware drivers installed and no compiz effects too (e.g. 3d cube).

:mad:

---

