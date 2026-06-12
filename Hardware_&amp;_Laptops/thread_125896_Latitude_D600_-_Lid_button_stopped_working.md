---
title: "Latitude D600 - Lid button stopped working"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by hornett on 2006-02-05
My laptop no longer dims or locks the screen when you close the lid.

This had been working for several months with no problems. I haven't upgraded any packages for a while, or changed any related settings.

Running, lid.sh this is what I get:

```
retro@d600:/etc/acpi$ sudo ./lid.sh
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver-command: can't open display :0
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver-command: can't open display :0
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xset:  unable to open display ":0"
retro@d600:/etc/acpi$

```

Any help, much appreciated!! :confused: :confused: :confused:

---

### Post by hornett on 2006-02-05
I got fed up with this not working, so as a temporary fix - I rewrote the lid.sh script to simply dim the screen backlight.

```
#!/bin/sh

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
        vbetool dpms off
else
        vbetool dpms on
fi

```

:D

---

### Post by Matt Yun on 2006-08-05
I also have a D600, still running Breezy.  This is what I did:

1) run 'xset dpms force off'

2) Edit /etc/X11/xorg.conf, and under Section "Monitor" add:
		Option "DPMS" "true"

---

### Post by jchau on 2006-09-30
:D We both had almost [identical problems and the same solution!]("http://ubuntuforums.org/showthread.php?t=134319").  But someone on my thread found a way to make the screen lock too (if ur running X) (I haven't tested that feature).

---

