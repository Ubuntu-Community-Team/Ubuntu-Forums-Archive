---
title: "GDM Refresh Rate"
date: 2005-11-17
forum: General Help
---

### Post by raf.kaplon on 2005-11-17
I have a ViewSonic G90f 19" that I have running at 1280x1024 @ 75Hz. It's capable of running 1280x1024 @ 85Hz.

Setting up the monitor and the resolution and refresh rates wasn't and isn't a problem but what I'd like to know is why the GDM login screen chooses to use 1280x1024 @ 85Hz. I've set 1280x1024 @ 75Hz to be the default in the gnome configuration editor but GDM seems to always choose the 85Hz option. Is there a way to set the GDM resolution and refresh rate other than it reading the default, which doesn't seem to work in my case? I've spent quite a bit of time looking around for an answer.

Thanks in advance,

-Raf

---

### Post by Remmelas on 2005-11-17
The gnome configuration only takes effect when you are logged into gnome.
an easy fix is to 
1) log into gnome
2) fire up xvidtune in a terminal
3) click the "Show" button to make xvidtune print a modeline to the terminal
4) add that modeline to you xorg.conf file

an example for syntax from my own xorg.conf
```
Section "Monitor"
        Identifier      "KDS XF-7s"
        Option          "DPMS"
        Modeline        "1024x768" 78.75 1024 1040 1136 1312 768 769 772 800
EndSection
```

---

### Post by raf.kaplon on 2005-11-17
I'll try it as soon as I get home... Thanks.

-Raf

---

### Post by raf.kaplon on 2005-11-17
Works great! Thanks again,

-Raf

---

