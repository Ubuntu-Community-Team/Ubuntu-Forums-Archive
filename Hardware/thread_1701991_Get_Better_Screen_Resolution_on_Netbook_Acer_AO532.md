---
title: "Get Better Screen Resolution on Netbook Acer AO532h?"
date: 2011-03-07
forum: Hardware
---

### Post by apernix on 2011-03-07
I am using 10.1 inch Netbook Acer AO532h with dual boot Ubuntu 10.10 and Win7. As we know that most of the 10 inch netbooks available right now on the market ship with a standard resolution of 1024x600px that are incompatible with some GUI application that had been setup to using default resolution 1024x768.

Previously i've tried to remove this limitation in my Win7 OS, and found [this articel]("http://www.netbooklive.net/how-to-get-better-resolution-on-your-standard-10-inch-netbook-2772/") that working perfectly.

However, when i try to do the same on my Ubuntu find a problem because i can't find file xorg.conf which normally must be edited to adjust screen resolution. After doing some search at google, i've found several articel related to this problem but no one working perfectly for me.

As far, i was try xrandr method which can work using panning method but this is not exactly what i want. Adding new mode seems to be the perfect one for me, but i get this error:
```

aper@aper-netbook:~$ gtf 1024 768 60

  # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

aper@aper-netbook:~$ xrandr --newmode "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
aper@aper-netbook:~$ xrandr --addmode LVDS1 "1024x768_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26
aper@aper-netbook:~$ 

```

There is another method that generate xorg.conf by running ```
X -configure
``` command in recovery mode, but it seems will not working because at first we must add new resolution mode as above to use this method.

It is something wrong with my step above or anyone have better solution for this?

Thanks in advance.

---

### Post by hiltun on 2011-07-29
I'm running 11.04 on an Asus T101MT and I would to be able to change the screen res as well.

Thanks,

---

