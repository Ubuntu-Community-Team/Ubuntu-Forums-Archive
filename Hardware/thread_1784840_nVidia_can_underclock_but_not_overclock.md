---
title: "nVidia can underclock but not overclock"
date: 2011-06-17
forum: Hardware
---

### Post by sakishrist on 2011-06-17
Hello all,

I came across a strange issue while I was tweaking my nVidia GeForce 9600M GT (it is on an HP Pavilion dv5 1080ev laptop). 

My goal is to save some more battery, since my laptop drains a 12-cell battery amazingly fast.

The thing is, I can underclock as much as I want but when I decide to set to some higher frequency than the last set, the slide-bars just jump to the last setting. That also means I can not overclock at all (not that I need to but my out-of-pure-curiosity attempt failed).

The way I got to the frequency settings is by editing the "/etc/X11/xorg.conf" file and adding Option "Coolbits" "1" under the "Device" section. Then I configure the frequencies from "Clock frequencies" under "GPU 0" from the nVidia X Server settings.

Could this be just a GUI issue/bug?

Thanks a million!

PS: I use Ubuntu Natty x64 with the Classic Ubuntu (gnome).

---

### Post by sakishrist on 2011-06-18
bump

Please someone :(

---

### Post by sakishrist on 2011-11-14
bump

A few months later (with Ubuntu 11.10 - Gnome 3) and I still have this problem ... please help.

Thanks in advance

---

