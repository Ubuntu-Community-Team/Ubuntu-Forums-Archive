---
title: "AG Neovo K-A19 Unable to set to 1280x768"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by Saavik256 on 2007-06-27
Greetings!

I have recently installed Ubuntu 7.04 on my system:

Motherboard: ASRock K7S41GX
CPU: AMD AthlonXP 2200+ @ 1800 MHz
GPU: Sapphire Radeon X1650Pro AGP
+ a couple of hard disks, a dvd+/-rw drive

I got the Radeon drivers installed all ok, but I have another problem.
The display that I'm using is an AG Neovo K-A19, which happens to
be a widescreen display. Now the thing worked all well under WinXP
set to a resolution of 1280x768. Since a 4:3 picture looks distorted, I
would very much like to use the resolution mentioned above.

Here's what /etc/X11/xorg.conf says about the monitor:

```

Section "Monitor"
        Identifier      "K-A19"
        Option          "DPMS"
EndSection

```

I've tried using:

```

tomazz@tomazz-desktop:~$ gtf 1280 768 60

  # 1280x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
  Modeline "1280x768_60.00"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync

```

and then manually adding that line in the monitor definition in /etc/X11/xorg.conf
but when I selected that resolution, my monitor responded with

```

Attention! Input not supported!

```

Now, considering the fact that I've been able to run this monitor in the
specified resolution under Windows, I was wondering if there's any way
of making it run in such resolution under Ubuntu as well?



Cheers,

Thomas / Saavik256

---

