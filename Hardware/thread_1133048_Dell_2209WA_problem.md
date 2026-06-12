---
title: "Dell 2209WA problem"
date: 2009-04-22
forum: Hardware
---

### Post by italianguy on 2009-04-22
Hi everybody! I'm new to this forum.
I'm opening this thread because I have a problem: I've just bought a new monitor, a Dell 2209 WA but unfortunately I can't make it work on Ubuntu. When I start Ubuntu I got a message error that tells me to fix the resolution and the hz. I unmounted my monitor and I mounted back my old monitor to fix the resolution. Unfortunately that won't make it start anyway. What can I do?

Thank you!

P.S. I am so sorry for speaking so bad. :(

---

### Post by ajgreeny on 2009-04-22
First try starting in recovery mode from the grubmenu and choose xfix when you see the options menu appear.  This should detect your new monitor.  If it does not work, you may need to edit your /etc/X11/xorg.conf file manually with the right data for your screen in the pattern of my xorg.conf file.  My original xorg.conf had almost nothing in it, just lines with "Configured device" so I added my screens resolution and refresh values found in the specs of the monitor.  The format needs to be in this form:-
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```Note:  I have ommitted all the un-necessary info at the top of the file for clarity's sake.
I hope this will help you.  Use ```
gksudo gedit /etc/X11/xorg.conf
``` to edit the file, but do a backup first, just in case.  Save the file then try  restarting the machine, and hopefully-----.  Good luck.

---

### Post by ajgreeny on 2009-04-22
> **enkw22 said:**
> I'm new user from here
So what are we supposed to do about it?

---

### Post by italianguy on 2009-04-23
Thank you ajgreeny! I solved the problem. I just needed to choose xfix in recovery mode. Guess it was easier than I thought. Thanks again.

---

