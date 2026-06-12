---
title: "Refresh Rates"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by Rickie on 2005-06-08
Hi guys, On windows i can use 1152*864 @ 72hz (Looks better then 75, 75 is really fuzzy) and on Ubuntu i can only do 75, and i know i have the nvidia drivers as i get that nVidia logo at startup, anyway i can force Ubuntu to use 72hz?

Thanks in advance :)

---

### Post by skoal on 2005-06-08
I nice little tool for such occasions as this is "gtf".

For your particular resolution/vert. refresh rate:

```
skoal@morpheus://~ $ gtf 1152 864 72 -x

  # 1152x864 @ 72.00 Hz (GTF) hsync: 64.87 kHz; pclk: 99.64 MHz
  Modeline "1152x864_72.00"  99.64  1152 1224 1344 1536  864 865 868 901  -HSync +Vsync

```

1. Just add that modeline in /etc/X11/xorg.conf like so:

```
Section "Monitor"
        Identifier      "Generic Monitor"
        VendorName      "Sony"
        ModelName       "G400"
        Option          "DPMS"
        HorizSync       30.0 - 107.0
        VertRefresh     48.0 - 120.0
[...]
# 1152x864 @ 72.00 Hz (GTF) hsync: 64.87 kHz; pclk: 99.64 MHz
  Modeline "1152x864_72.00"  99.64  1152 1224 1344 1536  864 865 868 901  -HSync +Vsync
[...]
EndSection
```

2. Log out of DE (Gnome, KDE, or whatever)...
3. Restart X with ctril-alt-bkspc
4. Log back in and select new mode.  Booyah!

\\//_

---

### Post by Rickie on 2005-06-08
[QUOTE=skoal]I nice little tool for such occasions as this is "gtf".

1. Just add that modeline in /etc/X11/xorg.conf like so:


\\//_[/QUOTE]

How would i go about adding that? xorg.conf is read only, sorry if it's something obvious  ](*,)

---

### Post by skoal on 2005-06-08
oops!

sudo gedit /etc/X11/xorg.conf

* you only need to add that line which begins with "Modeline" to the proper section as I illustrated with my setup.  While you're at it though, if you haven't already added HorizSync and VertRefresh settings for your specific monitor, that might be a good idea too.

\\//_

---

### Post by Rickie on 2005-06-08
NM, Fixed! (I added it in the wrong place  ](*,) )

---

