---
title: "Touchpad is detecting my middle &quot;floating&quot; finger"
date: 2019-02-21
forum: Hardware
---

### Post by leow974 on 2019-02-21
Hi,

I read a lot about how to set up your touchap properly but I can't manage mine to work the way I want. What's happening is: when I move my pointer around and that my middle finger is to close to my forefinger, it is detected by the trackpad (even if it is not touching it) and that mess things up (jumping pointer and random stuffs). I tweaked my touchpad settings (playing with  xinput --set-prop 13 "Synaptics Finger" mostly) but I can't make any difference. I use a DELL Latitude E7440 and have the lastest Ubuntu release installed.

Cheers !

---

### Post by Risperix on 2019-02-23
I use the same laptop, my advice is to use the touch in minimun sensibility.

---

### Post by leow974 on 2019-02-25
Hi, thanks for the reply but setting the sensitivity to minimum does not help. Same thing happens but at some point my trackpad is not working anymore (except if I press the sh*t out of it).

---

### Post by &amp;wP*!) on 2019-08-14
Maybe extremely late: can you check the BIOS version by **sudo dmidecode -s bios-version**?
Check this version with the most recent one on [Dell site]("https://www.dell.com/support/home/us/en/04/product-support/product/latitude-e7440-ultrabook/drivers"). I know from a lot of posts of E7440 that BIOS upgrade fixed most of Touch/TrackPad issues.

---

