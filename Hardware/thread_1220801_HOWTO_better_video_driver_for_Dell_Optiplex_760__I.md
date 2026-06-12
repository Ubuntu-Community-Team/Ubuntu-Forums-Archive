---
title: "HOWTO: better video driver for Dell Optiplex 760 / Intel Eaglelike video card"
date: 2009-07-23
forum: Hardware
---

### Post by JW3 on 2009-07-23
I had installed Ubuntu 9.04 on an Optiplex 760. Everything went smoothly with the notable exception of the video drivers; the display worked, but was not perfect, the Compiz effect were not smooth and little glitches appeared now and then (sometimes some windows contents got garbled and you had to minimize and maximize the window to restore it).

This box features an Intel Video Chip reported by X to be

```

Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3

```

and by lspci to be

```

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

```

It turns out that in Ubuntu 9.10 is a much better, revised version of the intel driver. However, I did not wish to change to 9.10, and only install the intel driver. For this, I had to do the following:

[LIST=1]
[*] Install necessary packages:
[LIST]
[*] download packages manually from [http://de.archive.ubuntu.com/ubuntu/pool/main/](http://de.archive.ubuntu.com/ubuntu/pool/main/)
[LIST]
[*] libdrm-intel1-2.4.11-1ubuntu1
[*] xserver-xorg-video-intel-2:2.8.0-0ubuntu1
[/LIST]
[*] install manually using dpkg -i packagename
[/LIST]

[*]Unfortunatelly, after installing the new intel drivers, the X server decided to use VESA instead of intel, and the resolution was completely wrong. To deal with this, I had to edit my /etc/X11/xorg.conf to specifically tell the X server to use the intel driver. Here is my xorg.conf:

```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "IntelEaglelike"
EndSection

Section "Device"
        Identifier      "IntelEaglelike"
        Driver          "intel"
EndSection

```
[/LIST]


Now the display is perfect.

---

### Post by jas007 on 2009-12-19
Cool, thanks for this post. Can't wait to try this out. I had the same issues with 9.04 on the same box, the issues still exist on 9.10, just not as bad. - I will fill you in with the results.
jas

---

### Post by marcusR33 on 2010-03-01
In which folders will I find the packages to download? Thanks.

---

