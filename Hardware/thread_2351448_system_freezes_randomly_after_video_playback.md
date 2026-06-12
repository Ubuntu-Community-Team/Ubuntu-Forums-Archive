---
title: "system freezes randomly after video playback"
date: 2017-02-03
forum: Hardware
---

### Post by drechsel on 2017-02-03
[FONT=arial]Hello,

this is my system [/FONT][COLOR=#636363][FONT=Menlo][FONT=arial]ubuntu 16.10, gnome desktop, 4 GB RAM, 2x3 GHz core duo, video card nvidia GT 630, 2 monitors.
Trouble began when I installed the 2nd monitor - both are DVI, one has a DVI cable, the other a HDMI->DVI adaptor cable.

Since then I'm really suffering from random system freezes - a few times a day. These especially appear after playing back a video using VLC or totem, after resume from suspend - and randomly at other opportunities.
I can then log in via ssh from another computer, killing Xorg will make the machine usable again most occurencies.

I cannot simply log out, xserver will crash and drop me to terminal.
I tried to purge and reinstall all nvidia drivers, tried the nouveau, tried to reinstall xorg.

Attached is the latest log file from /var/crash - which probabely is of limited use...
What can I do?

Cheers,Wolf





[/FONT]
[/FONT][/COLOR]

---

### Post by drechsel on 2017-02-04
I tried a dpkg-reconfigure xserver-xorg.

Now when booting the machine, it will hang at the "Your machine is runnig in low-graphics mode". It will not react, but I can ctrl-alt-F1 go to the terminal, log in and successfully get to the gnome desktop with the "startx" command.

---

