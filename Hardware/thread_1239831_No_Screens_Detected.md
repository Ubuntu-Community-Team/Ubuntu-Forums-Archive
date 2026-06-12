---
title: "No Screens Detected"
date: 2009-08-13
forum: Hardware
---

### Post by freddiespagheti on 2009-08-13
I just recently installed Xubuntu (Jaunty) onto an old PC through Wubi. I'm hoping to eventually transfer it to a second hard drive that the computer is already equiped with.

Trouble is though, I can't get it to display a desktop - just the command line. I did quite a bit of searching on this, tried three different solutions, and none of them worked. I didn't really expect them to, though, because they were for different hardware. I'm fairly certain the issue is with my graphics card but I don't know what to do.


    Specs:
The computer runs Windows XP with 192 MB RAM
It's a little slow, but now problems.

The computer is probably from about the year 2000

For Devices, Windows says I have:

Display Adapters:
    Diamond Multimedia Fire GL1000 Pro

The monitor is kind of old too could that be the problem?




    Symptoms:
Just before the request for a command line login it says:
```
Loading, please wait...
usplash: Setting mode 650x480 failed
screen init failed

Ubuntu 9.04 ubuntu tty1

ubuntu login:
```If I enter 'startx' I get:

```

(EE) VESA(0): Driver can't suport depth 24
(EE) Screen(s) found, but none have a usuable configuration.

Fatal server error:
no screens found

```
If I go to /etc/X11/xorg.conf it says (minus the comments):
```

Section    "Device"
               Identifier       "Configured Video Device"
               Option           "UseFBDev"                 "true"
EndSection

Section    "Monitor"
              Identifier         "Configured Monitor"
EndSection

Section     "Screen"
               Identifier         "Default Screen"
               Monitor            "Configured Monitor"
               Device             "Configured Video Device"
EndSection

```
Any ideas on what to do?

---

### Post by freddiespagheti on 2009-08-14
Bu-bump.

---

