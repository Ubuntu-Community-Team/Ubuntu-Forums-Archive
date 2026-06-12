---
title: "Increase Screen resolution to 1024 x 768"
date: 2010-05-25
forum: Hardware
---

### Post by habib2535 on 2010-05-25
Anyone can help me to progress here please ? i am stuck since 7 days on this :

I just installed the latest ubuntu 10.04 on a Toshiba-Tecra having "Trident Microsystems Cyberblade XP4m32" Monitor. After install resolution is defaulted to 800x600. I followed a method advised in some threads (arount xrandr and cvt) to increase the size (my laptop works with 1024x768 under XP). This was done OK and I obtained the resolution 1024X768 appearing in the drop list resolution options of the Monitor preferences but when I select the option if fails. Alternatively, when I execute
$ xrandr --output default --mode 1024x768_60.00
i got the message "xrandr : screen cannot be larger than 800x600 (desired size 1024X768)

I also saw a possible fix proposing to add "HorizSync 31.50-48.00" in Xorg.conf but I then I DO NOT have such a file in my /etc/x11/ after ubuntu install (supposing that this will fix my problem !!!)

Thanks to help me to progress

---

### Post by anglican on 2010-05-26
> **habib2535 said:**
> Anyone can help me to progress here please ? i am stuck since 7 days on this :

I just installed the latest ubuntu 10.04 on a Toshiba-Tecra having "Trident Microsystems Cyberblade XP4m32" Monitor. After install resolution is defaulted to 800x600. I followed a method advised in some threads (arount xrandr and cvt) to increase the size (my laptop works with 1024x768 under XP). This was done OK and I obtained the resolution 1024X768 appearing in the drop list resolution options of the Monitor preferences but when I select the option if fails. Alternatively, when I execute
$ xrandr --output default --mode 1024x768_60.00
i got the message "xrandr : screen cannot be larger than 800x600 (desired size 1024X768)

I also saw a possible fix proposing to add "HorizSync 31.50-48.00" in Xorg.conf but I then I DO NOT have such a file in my /etc/x11/ after ubuntu install (supposing that this will fix my problem !!!)

Thanks to help me to progress
Boot into recovery mode, when you get to the command line type:
```
sudo Xorg -configure
```which will create a default /etc/X11/xorg.conf file. Add the lines:
```
        HorizSync       31.0 - 70.0
        VertRefresh     40.0 - 75.0
```to the Monitor section then reboot.

H

---

### Post by habib2535 on 2010-05-26
Thanks... It worked !!!

... and that was so simple !

---

