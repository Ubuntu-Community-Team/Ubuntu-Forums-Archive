---
title: "Suggestions to a newbie"
date: 2008-11-12
forum: General Help
---

### Post by Gabbsmo on 2008-11-12
I am ttotally new to linux have a quite old PC-box that I want to run Ubuntu and Windows 2000 SP4 on in a dualboot.

Specs

PIII 733 Mhz
256 Mb RAM
Geforce 2 MX 32 Mb

I want to try installing with the alternate CD using this setup:

```
linux-generic acpi, acpid language-pack-en
sudo aptitude install xorg fluxbox fluxconf slim dillo xfe aptitude
startx
sudo apitude install libstdc++5
wget -c ftp://ftp.mozilla.org/pub/firefox/releases/1.5.0.12/linux-i686/en-US/firefox-1.5.0.12.tar.gz
sudo tar zxvf ~/firefox-1.5.0.12.tar.gz -C /opt
```

What verision/dist do you recomend? I'm intressted in Ubuntu, xUbuntu and Fluxubuntu.

I failed installing xubuntu with the live-cd, it hung.

I want to use the computer for simple office tasks, music/video playback. DVD-ripping/burning and bittorrent.

---

### Post by oldos2er on 2008-11-12
The Live CD requires 384MB RAM to run. You might want to look into Vector Linux standard; it has xfce, but in my opinion it is snappier than Xubuntu.

---

### Post by philinux on 2008-11-12
I'd try the xubuntu alternate install.

---

### Post by mikjp on 2008-11-12
Both Ubuntu and Xubuntu are too heavy for that hardware. I write this on a P1000 / 256 MB. I first tried to use Xubuntu for some weeks, but now I've used Vector Linux 5.9 and am very happy with it. Zenwalk is another newbie friendly and lightweight distro that should run well on your hardware. Debian should be fine, too.

Greetings,

mikko

---

### Post by philinux on 2008-11-12
My girlfriend is running ubuntu on my old p3 500mhz 320meg ram. It's not zippy but it does the job for internet and office.

---

