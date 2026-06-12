---
title: "Conexant Audio Problems- Toshiba C655D-S5041"
date: 2011-03-26
forum: Hardware
---

### Post by NickKourpias on 2011-03-26
I've installed Ubuntu in a dual-boot on my Toshiba C655D-S5041. I have everything working except one thing. The audio card doesn't seem to realize that I have a headset plugged. I've tried to install the Linux version of the Conexant audio card drivers, but to no avail. Please help!

---

### Post by Yellow Pasque on 2011-03-27
```
echo "options snd-hda-intel model=ideapad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
[http://www.linlap.com/wiki/toshiba+satellite+c655d](http://www.linlap.com/wiki/toshiba+satellite+c655d)
AFter that, restart and remember to adjust headphone volume before rupturing your eardrums (not that I've ever done that...).

---

### Post by lidex on 2011-04-03
Nice. I'm trying not to laugh but ezra brooks won't let me.

---

