---
title: "[SOLVED] 100% FULL solution to Gutsy audio problem on Toshiba a135-s4727 or 4527"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by mimagabooks on 2007-11-09
I have worked on two Toshiba a135-s4727 and two of the 4527 as well as a 2234. But so far only the models ending in 27 have broken.

But after a lot of searching I finally found a solution download and install--the realtek High Def Driver for linux.

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

However the only way I and several others have made this work is as follows.

1. Start with a fresh install of Gutsy (k,u,x whichever you like)

2. Run the first update with your package manager do not install other software. (except a compiler)
[HTML]
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
[/HTML]

3.Unzip and install the Realtek High Def Driver (or as realtek calls it "High Definition Audio Codecs")
[HTML]
cd /... (to folder) 
sudo ./install
[/HTML]

This will install the alsa drivers (1.0.14), your sound wheel will seem to work (1-100%).
Each program will control its own volume level.

Note: If you have already done the driver install steps above and it didn't work in gutsy I will say the only way this realtek driver has work for us is a fresh install.

If there is another way that makes every thing work in gutsy please let me know.

For a fix on 7.04 and earlier click this link.
[http://ubuntuforums.org/showthread.php?t=539595&highlight=A135](http://ubuntuforums.org/showthread.php?t=539595&highlight=A135)

---

