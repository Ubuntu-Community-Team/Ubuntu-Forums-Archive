---
title: "Samsung N150 Brightness"
date: 2015-03-29
forum: Hardware
---

### Post by btj_79 on 2015-03-29
Hi guys,

I'm having a issue with my brightness control on Ubuntu 14.04, the keyboard brightness controls are not working. I found information on another site that said;
> 
[QUOTE]by adding the following in /etc/X11/xorg.conf.d/20-intel.conf:  

> Section "Device"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        Identifier "card0"
EndSection

[/QUOTE]

should fix it but this file does not exist. I assume creating it would be pointless as nothing is currently looking at it. I have also already installed samsung tools and this has not fixed the issue. Any help would be appreciated.

Thanks,
Daniel

---

### Post by jeremy31 on 2015-03-29
But if you create it, Ubuntu will find it, only one way to see if it helps.  It may not help if you have hybrid graphics

---

### Post by btj_79 on 2015-03-29
Yeah I feel like an idiot now..that worked. Thanks!!

---

