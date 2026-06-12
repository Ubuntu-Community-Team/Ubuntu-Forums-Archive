---
title: "DPMS (display power management) Problems in Kubuntu Edgy"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by jdunn on 2006-10-27
In Dapper, I had to edit the xorg.conf file to get DPMS running so my display would power-off after 30 minutes of inactivity.  Now, I'm using a fresh install of Edgy and I can't get DPMS to work.  I'm not sure if the new xorg, new nvidia drivers or linux kernel is the problem.  I've tried enabling DPMS in System Settings>Monitor&Display too.  Help!!

*Update*
I also tried 'xset +dpms', 'xset dpms 0 0 60', 'xset dpms 60 0 0' and they only blank the screen...they don't change the display power mode.

I'm using a Gforce 5600 with the 8774 glx drivers.

---

### Post by jdunn on 2006-10-28
bump.
SOMEONE AT LEAST TELL ME IF THEY HAVE DPMS WORKING IN EDGY.

---

### Post by jdunn on 2006-10-28
Please help me out.  I just tried this and all it does is blank my screen without shutting off the display:
xset dpms 300 600 900
xset -q

```
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  250    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfe5ef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  20/10    threshold:  2
Screen Saver:
  prefer blanking:  no    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Standby: 300    Suspend: 600    Off: 900
  DPMS is Enabled
  Monitor is On
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log

```

I also ran the live CD and tried this, in which case DPMS worked.  This leads me to believe it may have something to do with the NVIDIA drivers???  Problem is, no one is responding here.  I do help people solve THEIR problems on this forum so I'd appreciate some help.

---

### Post by jdunn on 2006-10-28
*Bump*
Uninstalled Nvidia glx driver, disabled hyperthreading in kernel, removed NTP tools...assuming they might cause DPMS not to work.  It made no difference.

As usual, no one on these forums has answers.

---

### Post by jdunn on 2006-10-28
*bump*

---

### Post by Feanor on 2006-11-09
I've the same problem, I'm trying to modify something if works I will tell you.

Look here
```
fabio@athlon:~/.kde/share/config$ more displayconfigrc
[General]
targetgamma=2.0

[Screen0]
dpmsEnabled=on
dpmsSeconds=18000
height=1024
reflectX=0
reflectY=0
refresh=75
rotate=0
width=1280

```

---

### Post by alonso on 2006-11-10
Hey, thanks for this info. I had the dpms option off in this file even though I have DPMS set on in the KDE control panel. So this seems like a KDE bug?

---

