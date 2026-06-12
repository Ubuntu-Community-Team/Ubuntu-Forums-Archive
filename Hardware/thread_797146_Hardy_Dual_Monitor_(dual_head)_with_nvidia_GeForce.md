---
title: "Hardy Dual Monitor (dual head) with nvidia GeForce 9800 card"
date: 2008-05-17
forum: Hardware
---

### Post by Oldmartian on 2008-05-17
Does anyone have any experience with dual head on U8.04?  I've got one monitor running at 1680x1050, but I can't get Ubuntu to see the second monitor.  I'm using the latest driver from Nvidia.

Thanks.

---

### Post by chewearn on 2008-05-17
Back-up your xorg.conf file in case it got messed up and you have to revert to the currently working one:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Next, run nvidia-settings with sudo:
```
sudo nvidia-settings
```Click "X Server Display Configuration" on the left pane.  Here you can set-up dual screens (it will take some experimenting to get what you want and unfortunately, I don't think it's not the most intuitive application).

Once you are satisfied with the results, click "Save to X Configuration File", quit  nvidia-settings, and reboot your PC.

.

---

### Post by DougAlder on 2008-05-24
I've got dual monitor working now with nvidia in x configuration but I'm having a weird problem with my mouse - it does not want to move from the laptop screen to the Acer LCD monitor - occasionally I can suddenly get it to go there but then I can't get it back. I can't find anything in nvidia-settings that would account for this. Anyone have any ideas?

---

