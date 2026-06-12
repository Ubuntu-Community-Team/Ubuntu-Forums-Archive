---
title: "Getting Video and Monitor to Work Correctly"
date: 2008-11-06
forum: Hardware
---

### Post by tobey1 on 2008-11-06
I have the following video card:
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc 3D Rage Pro AGP 1X/2X [1002:4742] (rev 5c)

And I do not see this in anything in Ubuntu 8.10.  Also, I have to manually set my screen resolution every time I login.

Here is my xorg.conf

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

As you can see nothing specific to my ATI card.  Any help would be greatly appreciated.

---

### Post by PendragonUK on 2008-11-06
Try searching the forum for "Black Screen of Death" these threads should give you some pointers. There are multiple conversations talking about this or very similar issues. Sorry not to be any direct help but you are not alone.

---

### Post by tobey1 on 2008-11-06
Thanks...I am not getting a Black Screen.  I get standard 800x600 resolution everytime I boot up.  I will look at "Black Screen of Death" for more info.

---

### Post by pelle.k on 2008-11-06
Backup xorg.conf
```
cp /etx/X11/xorg.conf .
```
Install displayconfig-gtk
```
sudo aptitude install displayconfig-gtk
```
Run it
```
sudo displayconfig-gtk
```

To be honest, displayconfig sucks a little bit, but if you just want to do small modifications, it'll probably do.

---

### Post by tobey1 on 2008-11-06
Thanks I am good to go now.

---

