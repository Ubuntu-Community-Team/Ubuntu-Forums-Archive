---
title: "Can't see all my screen+resualation (Nvidia)"
date: 2010-10-28
forum: Hardware
---

### Post by Need not to know on 2010-10-28
I have Ubuntu 10.10, I installed nvidia current driver from ubuntu repository, but the resolution was 1024 768 and I want it 1280 1024, I tried 2 things:
[LIST=1]
[*]Added a "Modeline" to "xorg.conf", didn't work, so I deleted it.
[*]I read a way to add new resolution, but in "xrandr --newmode, I got an error, so it didn't work too.
[/LIST]
I reboot my system but I got this:
[IMG]http://dl.dropbox.com/u/1824044/Screenshot.resized.png[/IMG]
If I removed the driver it's all be fine, So I tried to install the new driver from this [link]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html"), after installing the driver and rebooting my system, I got the same error in the picture, but when I disable the effects (you can see that the effects don't work fine in the picture) I can see all the screen!

My video card is 7300 GT, it works fine with effects usually.
My xorg.conf:
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

Q1\ How to make the effects work and I can see all the screen?
Q2\ Is there another way to use 1280 1024?

and thanks :)

---

### Post by dasan on 2010-10-28
Try with ubuntu's own restricted driver manger...
i think it will help

---

### Post by Need not to know on 2010-10-28
If you mean "Additional Drivers" (or "Hardware Manager" in the past), I actually did:
> I installed nvidia current driver from ubuntu repository

:)

---

### Post by Need not to know on 2010-10-28
Finally, I fixed the first problem, from "CompizConfig Setting Manager" then "General Options" then "Display Setting" tab, and check "Detect Outputs".

But the second question still unfixed:
> Q2\ Is there another way to use 1280 1024?

---

### Post by dasan on 2010-10-29
as far as i know Normally resolution fix is done from  xorg.conf only

---

### Post by Need not to know on 2010-10-29
This is my xorg.conf:
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
EndSection
```
But there is no 1280 1024 when I want to change the resolution.
If there is no other ways, I can live with 1024 768.

Arigato Gozaimasu.

---

### Post by Need not to know on 2010-10-29
Fixed, \\:D/
from [here]("http://www.linuxac.org/forum/showthread.php?45244-%E1%C7-%C3%D3%CA%D8%ED%DA-%E3%D4%C7%E5%CF%C9-%DF%C7%E3%E1-%C7%E1%D4%C7%D4%C9-%E6%C7%E1%E3%C4%CB%D1%C7%CA-%CA%DA%E3%E1-%C3%C8%DA%C7%CF-%C7%E1%D4%C7%D4%C9-(Nvidia)"), first I removed my xorg.conf (renamed to xorg.conf.backup) then in terminal "nvidia-xconfig", then I added this lines to "Monitor" section:
```
    Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    Modeline "1152x864_65.00"   88.75  1152 1216 1336 1520  864 867 871 900 -hsync +vsync
    Modeline "1152x864_70.00"   96.75  1152 1224 1344 1536  864 867 871 902 -hsync +vsync
    Modeline "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
    Gamma        0.75
```
and changed this:
```
Section "Monitor"
    Identifier     "Monitor0"
```
to this:
```
Section "Monitor"
    Identifier     "Configured Monitor"
```
save the file and reboot, and finally I got 1280 1024 :D

thanks for Ehab, and thank you dasan for trying to help :)
Bye.

---

