---
title: "Refresh Distribution"
date: 2008-05-22
forum: Hardware
---

### Post by jamesattard on 2008-05-22
Hi guys, up till a couple of days ago, my laptop with Ubuntu 9.04 was working perfectly fine. However my laptop screen needed to be replaced and I was temporary assigned a quasi-similar laptop model and we swapped the harddisks so I could continue work uninterrupted. There were some minor hardware differences including graphic card (nvidia) instead of the original intel. Needless to say, I had to configure for the new hardware and was working fine. The problem arose when I got back my original laptop - it seemed that the previous configurations were not compatible and now I have the following issues:

1) Gnome Network Manager not working as it should and I have to manually set wi-fi with iwconfig instead of being automatically assigned. Same goes for eth0!!
2) Although I can see movies and webcam is working fine, I'm getting the error: Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0" when I fire programs like mplayer, cheese, etc. and I feel that the performance degraded when I use the webcam.

Instead of trying to fix or trying to find how to revert to the original configuration, is there a way how to re-install the distribution with apt-get seamlessly?

---

### Post by prshah on 2008-05-22
> **jamesattard said:**
> Instead of trying to fix or trying to find how to revert to the original configuration, is there a way how to re-install the distribution with apt-get seamlessly?

CAVEAT: The below commands are dangerous and I have no idea how they will affect your system, but they are related to your question.

There is no way to "reinstall" a distribution (in place installation, as reffered to by XP). However, you can try one or more of the following:```

sudo dpkg --configure -a
sudo apt-get install --reinstall ubuntu-desktop

```

My personal suggestion is that it will be easier to fix your problems. 

Lets start with display: Can you post your "/var/log/Xorg.0.log" file as an attachment?

---

### Post by jamesattard on 2008-05-23
Managed to fix the Xlib error by removing everything related to xorg and installing xorg again.

---

