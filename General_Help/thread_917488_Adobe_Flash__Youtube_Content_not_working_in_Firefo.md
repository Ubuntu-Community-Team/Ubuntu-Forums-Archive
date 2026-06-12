---
title: "Adobe Flash / Youtube Content not working in Firefox"
date: 2008-09-11
forum: General Help
---

### Post by splicer707 on 2008-09-11
:confused:

I did something wrong. 
Not sure what, but when I go to Youtube, example: [http://www.youtube.com/watch?v=gBWPf1BWtkw](http://www.youtube.com/watch?v=gBWPf1BWtkw)

I don't see the video, only a white block. :(

---

### Post by Bucky Ball on 2008-09-11
You need to install flashplayer.

First, go to Synaptics and find:

ubuntu-restricted-extras

Tick it, apply changes and it will install the packages. Also, you can open a terminal (Applications->Accessories->Terminal) and copy and paste this line by line, not all at once:

```
cd /tmp
wget [http://download.macromedia.com/pub/l..._070208.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz")
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```If that doesn't work, this one has been suggested as more recent version of flashplayer 10 but didn't work for me:

```
cd /tmp
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz
tar -xvzf flashplayer10_install_linux_081108.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```

If one of these last two works but you cannot get full screen, right click on desktop and set it to single colour. :)

---

### Post by splicer707 on 2008-09-12
Thank you :KS

Just trying your suggestion now.

---

