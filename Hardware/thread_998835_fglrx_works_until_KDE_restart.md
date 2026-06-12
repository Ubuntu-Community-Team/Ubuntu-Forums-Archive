---
title: "fglrx works until KDE restart"
date: 2008-12-01
forum: Hardware
---

### Post by sobranko on 2008-12-01
This is my configuration:
AMD Athlon64 3000+
2GB RAM
ATI X850XT AGP
Big screen SONY E430 CRT (1600x1200@75Hz max) - my Primary monitor - connected on VGA
Small screen Belinea CRT (1280x1024@75Hz max 1600x1200@60Hz in windows) - my Secondary monitor - connected on DVI (DVI-VGA adapter)
Connected TV with max 1024x768

Installed kubuntu desktop over ubuntu (version 8.04)

Gnome has slow 2D with fglrx driver (i could not work).Gnome has good 2D with open source drivers 
bud 3D is bad. I could not run in dual head mode under Gnome so i did not use secondary monitor.

I have installed KDE just to see how it works. It looked good so i decided to try
my luck and installed fglrx on it. I was surprised, graphics works good under KDE with fglrx 
(2D is still slower than open source drivers but it is OK).

Problem 1:
After KDE restart fglrx no longer works, low-graphics mode display shows up

Quick fix:
ALT-CTRL-F2
```
sudo aticonfig --initial -f
sudo reboot
```

After that fglrx works fine until next KDE restart.

I have analyzed Xorg logs (in /var/log/ Xorg.0.log and Xorg.0.log.old). When fglrx works (after aticonfig and reboot from console)
Xorg.0.log says that amdpcsdb was not found and that fglrx will generate it and after that he starts up. 
After KDE restart Xorg.0.log says that he is using xorg.conf.failsafe and Xorg.0.log.old says that he has found amdpcsdb and using it
but it also reports famous "PreinitDAL failed" error.

What caught my eye is that fglrx detected multiple screens (in both cases) and that he is putting screens 
in clone mode but when i fire up my secondary screen (when fglrx is running) i get "No signal detected" from it.

I googled for "PreinitDAL failed" and found that it can be caused by plugged TV so i did
```
sudo aticonfig --force-monitor=crt1,notv
```

Problem 1 solved - fglrx works after KDE restart

Problem 2:
fglrx works but both screens are in 1024x768@60Hz clone mode - very bad - can't work with that.

I downloaded AMD Catalyst Control Center which detected primary monitor with max resolution 1024x768@60Hz and 
secondary monitor at maximum resolution 1600x1200@60Hz. I thought that fglrx is confusing monitor with plugged TV so
i unplugged TV and restarted (complete restart).
This did not help, both monitors are in 1024x768@60Hz (clone) and AMD CCC still sees primary monitor as maximum 1024x768@60Hz.
So i thought that fglrx is probably confusing monitor connected on DVI out and monitor connected on VGA out as crt1. (VGA as crt2, 
DVI as crt1 but should VGA as crt1, DVI as crt2)

So i have tried:
```
sudo aticonfig --force-monitor=crt2,notv 
```

Problem 2 solved:

Monitors are in clone mode with primary monitor at 1600x1200 and secondary monitor in 1024x768 clone mode

Problem 3:
Primary monitor is at 1600x1200@60Hz I want 1600x1200@75Hz
This was probably because graphics card can't work with dual refresh rates in single-head mode.

Fix:
ALT-CTRL-F2
```
sudo aticonfig --initial=dual-head -f
```

Problem 3 solved, primary screen at 1600x1200@75Hz, secondary at 1280x1024@75Hz 

Problem 4:
I had 2 indepedant KDE desktops (i could move mouse from one to another).
I could not run glxinfo, glxgears, fglrxinfo, fgrxgears (3D apps hangs), AMD CCC.
KDE sees 2 screens at correct resolutions and refresh rates.

Fix:
I did not know what to do so i have tried
```
sudo aticonfig --dtop=horizontal --overlay-on=1
```
I don't know what it acually did but my problem is solved.


Primary screen is at 1600x1200@75Hz, secondary at 1280x1024@75Hz in clone mode.
I can start fglrxinfo, glxgears, fgrx_gears (all 3D apps works).
AMD CCC is reporting two screen in clone mode correctly identified (crt1 on VGA, crt2 on DVI), 
KDE sees only one screen in 1600x1200@75Hz but that is because they are in clone mode.

I can even play Nexuiz at high settings :-).
All apps works flawles.

Note: no compiz effects!

I hope this helps. Sorry about bad english.

---

