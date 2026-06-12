---
title: "Fixing xorg.conf through a live CD after 9.04 upgrade"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by alfachino on 2009-05-16
Hi,

I just upgraded to 9.04 and, no surprise, it did not go smoothly. It seems everything installed OK, but the graphics are not working and so I cannot boot. I tried booting from the LiveCD and everything works just fine. I am just unsure about how to use the info provided in the xorg.conf file during the live session in my normal session when I try to boot from disc. Any help would be greatly appreciated.

---

### Post by chellrose on 2009-05-16
Boot into recovery mode, and select "drop to root shell".  Then:

```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

If you have the xorg.conf from the Live CD saved, say, on a USB stick, then you can just copy it directly (assuming the computer has detected your USB stick on boot into recovery mode):

```

cp /media/disk/xorg.conf /etc/X11/xorg.conf

```

If that doesn't work, worst-case scenario you can edit the xorg.conf file by hand:

```

pico /etc/X11/xorg.conf

```

Make sure it contains exactly what's in the one from the CD, and then type Ctrl+X, Enter to save the file and exit.  Reboot into normal mode.

Alternatively, there is a way to get X to generate a new version of that file for you, but from what you've described it sounds as though the X-generated version is what's causing the problem in the first place.

---

