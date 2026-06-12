---
title: "No flash-player once in installed"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by emersonscorder on 2009-09-03
I tried ubuntu netbook remix liv eversion on a flash drive. While on the flash drive, i was able to install the plugin via firefox no issues. NOW since i've downloaded it says package not found (thats with the flash, gnash, or the third option which i dont recal). I even tried using terminal to instal flash, and i get package is no longer available but is referred by another package. I tried installing gnash. It said sucsessful but even after restarting, no flash player.

---

### Post by presence1960 on 2009-09-03
Are you just using the Live CD iso as a bootable image on a flash drive? or did you actually install Ubuntu to the flash drive?

if the latter uninstall all those instances of flash first. Then if you are running 32 bit ubuntu open a terminal and run ```
sudo apt-get install flashplugin-nonfree
```

or if you use 64 bit ubuntu see [here]("http://ubuntuforums.org/showthread.php?t=772490").

---

