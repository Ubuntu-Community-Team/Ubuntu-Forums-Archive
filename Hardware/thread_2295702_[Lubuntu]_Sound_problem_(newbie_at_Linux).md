---
title: "[Lubuntu] Sound problem (newbie at Linux)"
date: 2015-09-20
forum: Hardware
---

### Post by 2n2u on 2015-09-20
I have a laptop running Lubuntu 15.04. The problem is that my internal speakers are treated as headphones, and the volume of them is controlled by headphones bar at alsa. So if I plug headphones and unplug them, after there is no sound at speakers since the headphones volume value decreases to 0. So the problem is that the speakers are being recognized as headphones instead of speakers. Is there a way to fix this problem? :(



[IMG]http://puu.sh/kiubd/c60fba5d3d.png[/IMG]

[IMG]http://puu.sh/kiuwt/1a73bcd501.png[/IMG]

---

### Post by Yellow Pasque on 2015-09-20
Since this is very recent hardware, the first thing I would try is upgrading to latest sound module: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Off topic: you may want to run this command to make lspci a bit more informative:
```
sudo update-pciids
```

---

### Post by 2n2u on 2015-09-21
> **Temüjin said:**
> Since this is very recent hardware, the first thing I would try is upgrading to latest sound module: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Off topic: you may want to run this command to make lspci a bit more informative:
```
sudo update-pciids
```

I've upgraded to last module, same problem though :(

---

### Post by Yellow Pasque on 2015-09-21
Get more info. It may help (or not): [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by 2n2u on 2015-09-21
[http://www.alsa-project.org/db/?f=b64f1dde16a45cd95c543df8b92ca32044789b1e](http://www.alsa-project.org/db/?f=b64f1dde16a45cd95c543df8b92ca32044789b1e)

---

### Post by howefield on 2015-09-22
Thread moved to the "*Hardware*" forum for better support.

---

