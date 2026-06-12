---
title: "No sound problem"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by itsmathias on 2009-05-12
For some reason I have no sound on youtube for exemple and in VLC , but it works for MPlayer movie player. is there any way to fix this?

---

### Post by itsmathias on 2009-05-12
I tried this:
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin

[LIST]
[*]Restart Mozilla Firefox
[/LIST]
 Note: if sound doesn't work in Flash Player (for example on YouTube): 
 sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc
Change: 
 FIREFOX_DSP=""
To: 
 FIREFOX_DSP="aoss"

But for some reason I don't have the firefoxrc, so it didn't work

---

