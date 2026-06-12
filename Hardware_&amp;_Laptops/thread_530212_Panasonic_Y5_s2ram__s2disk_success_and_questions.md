---
title: "Panasonic Y5 s2ram / s2disk success and questions"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by bean1975 on 2007-08-20
Both s2ram and s2disk works, even from KDE. Caveat: if my non-standard 4G SD card is in the SD reader then neither works. This took same pain to reveal, I booted into init=/bin/bash listed all the modules, booted normal (without KDE) and compared the modules, and then binsearched...

The video driver is xserver-xorg-video-intel which is needed anyways for the 1400x1050 resolution. 

Question: which config file does s2ram use by default, because currently I need to add -f -a 3 every time. I would like to eventually get to the point where the lid closure triggers a suspend or even better an s2both.

Half answer: though I have not found an s2ram config, not even with strace s2ram 2>&1 |grep etc but [http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855) gives some good idea, editing /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux . Now, this is nice: I close my laptop and it sleeps into RAM.

---

