---
title: "sis 661 how to off just the laptop display"
date: 2010-04-10
forum: Hardware
---

### Post by bobbaluba on 2010-04-10
I kind of have two questions:

I just installed ubuntu 10.4 and everything ran smoothly. I'm using an old laptop as a server and i therefore want to be able to turn of the screen and use just an external one. The only problem is that the graphical screen configuration tool shows only one unknown screen.

I'm a complete noob to linux, and i was thinking this probably was some kind of driver issue. So i googled a bit and found some drivers here: [http://www.winischhofer.eu/linuxsispart4.shtml](http://www.winischhofer.eu/linuxsispart4.shtml)

i then installed the package sysctrl and after that i ubuntu has kept freezing during startup. It also freezes in recovery mode after selecting "repair broken packages" and drop to prompt.

Now, i didn't get to configure much before this happened, so i might just reinstall.. unless someone knows some clever tricks on how to fix this?

---

### Post by bobbaluba on 2010-04-10
This always happens! (i spend hours trying to solve a problem, and then, just minutes after asking on a forum, i find the solution)
Just now i inserted a live cd and deleted an xorg.conf file i created earlier. Now it doesn't crash anymore, and i'm able to boot properly.

Still i haven't solved my initial problem, though.
How do i disable just one monitor?

EDIT:
```
johan@tubes:~$ sudo lshw | grep VGA
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

EDIT2:
Googled a bit more, and found out the man page for the standard drivers: [http://manpages.ubuntu.com/manpages/jaunty/man4/sis.4.html](http://manpages.ubuntu.com/manpages/jaunty/man4/sis.4.html)

Mabye[B]
Option[/B] **"ForceCRT1"** **"**_boolean_**"**

could solve the problem, only problem is: where do i enter this?

EDIT3:
Okay, so i needed to create a xorg.conf file (there wasn't one there by default) i found someone elses config somewhere and just copied it and edited it a bit.
Here's my current xorg.conf:
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "sis"
    BusID        "PCI:1:0:0"
    VideoRam    128000
    Option        "UseFBDev"    "true"
    Option "EnableSiSCtrl" "yes"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

I was finally able to turn off the lcd screen by running sisctrl!

I'm still unable to choose higher resolutions, though...

---

