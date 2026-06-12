---
title: "no sound - Hardy on Toshiba laptop"
date: 2008-05-04
forum: Hardware
---

### Post by jynyl on 2008-05-04
Fresh install of Kubuntu 8.04 on Toshiba Tecra M9, but no sound (tried mplayer, KDE notifications, Kaffiene, etc).  From command line, mplayer reports cannot connect to sound server.

Audio is enabled in settings, and the linux-ubuntu-modules package is installed.
Sound worked fine on this laptop with Kubuntu 7.10.

Any tips or suggestions, please?

TIA

Peter

---

### Post by jynyl on 2008-05-08
Some more info;
lspci
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

aplay -l
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]

dmesg | grep -i alc
[   35.018002] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...

Strange that Hardy can't handle this device when Gutsy did sound just fine.

TIA

---

### Post by jynyl on 2008-05-10
Running this command seems to get sound working ...

```
sudo /etc/init.d/alsa-utils reset
```

this hint from ...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209047]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209047")

---

