---
title: "Unity working slowly"
date: 2013-03-11
forum: Hardware
---

### Post by rounder8 on 2013-03-11
I have a fresh copy of Ubuntu 12.10 (64bit) on my Lenovo W500. I installed all the updates. Hardware listing: [http://paste.ubuntu.com/5602371/](http://paste.ubuntu.com/5602371/)

The problem is that Unity takes forever to respond to commands: several seconds to open dash and every letter I type comes with a lot of latency. I've tried installing CompizConfig Settings Manager but I cannot figure out what to disable to make Unity faster. How can I speed up Unity? Perhaps installing proprietary drivers would boost the performance?

---

### Post by rounder8 on 2013-03-11
I tried to install proprietary drivers following the instructions from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

```


sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
sudo apt-get remove --purge fglrx fglrx-amdcccle
sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates
sudo apt-get install fglrx fglrx-amdcccle
sudo aticonfig --initial
```

Interestingly, I don't have /etc/X11/xorg.conf to begin with.

I get error when I type command "aticonfig": 
aticonfig: No supported adapters detected

Does that mean that my graphics adapter is not supported anymore?

lspci | grep VGA shows:
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV635 [Mobility Radeon HD 3650]

---

### Post by ibjsb4 on 2013-03-11
I have not had to deal with this problem, but thought this might help.

[http://ubuntuforums.org/showthread.php?t=2013413](http://ubuntuforums.org/showthread.php?t=2013413)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Radeon+HD+3650+12.04&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Radeon+HD+3650+12.04&sa=Search&cof=FORID:9)

---

### Post by rounder8 on 2013-03-12
I think the culprit here is 3D rendering combined with old GPU. I tried some other distros and I didn't have performance issues (for example KDE works fine). Perhaps Ubuntu 12.04 would work better on an old computer.

---

