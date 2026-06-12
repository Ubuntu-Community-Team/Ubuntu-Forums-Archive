---
title: "Mouse pointer does not appear"
date: 2014-01-26
forum: Hardware
---

### Post by javigrisalena-q on 2014-01-26
Hi everybody,

I am trying to install ubuntu on an old PC to a friend. The last attempt I've done has been with xubuntu, for being lighter, but I've tried it with ubuntu and kubuntu with the same result.

Everything works perfectly but the mouse pointer does not appear. I think it's a problem with the graphics card and the X server, so I could find on google. I tried with an older version of ubuntu, 9.04, and in this case the cursor works correctly, but I have problems with wifi and it is a version that is no longer supported.

Once installed xubuntu, I have also tried to install the proprietary drivers, but in this case when it start the graphical environment, nvidia logo appears and gets stuck there.

The computer is an AMD Atthlon 64 3000 with a NVIDIA GeForce FX 5500 256 Mb.

Any help would be appreciated.

Thanks

---

### Post by ibjsb4 on 2014-01-26
You did not say what your running so I assume its 13.10.  Try the LTS version of Xubuntu (12.04).

---

### Post by Yellow Pasque on 2014-01-26
Perhaps something is wrong with cursor accel. Try making an /etc/X11/xorg.conf file with following contents:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nouveau"
        Option         "HWCursor" "off"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen" 
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```

---

