---
title: "radeon 9250 and feisty..."
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by botulismo on 2007-04-20
I have a radeon 9250 and I just upgraded to feisty... When my computer went to reboot (i'm assuming most people know what happened) it went to the terminal screen... after tinkering around a little bit I enabled the open source "ati" driver, hit startx, and my desktop went up.

So... I really don't want to use this driver as I prefer 3d acceleration to eye candy. If I uninstall the xorg-driver-fglrx package and then get the compatible driver from the ati website and build it myself would it work okay? Or... would I be able to get the old (edgy) package and install that one and just watch update manager like a hawk and not let it update the drivers for me?

Any ideas or suggestions? I figure trying to find a solution is better than whining too much more.

---

### Post by whatever on 2007-04-20
1. fglrx does NOT support radeon 9250 anymore
2. the "ati" driver should provide 3d acceleration

---

### Post by botulismo on 2007-04-20
1. I'm NOT asking to install the current fglrx driver. If you'd read my post, you would have figured out that I had gotten that far already. I am asking if I can go to the ATI website, get the 8.28 driver, and install it directly from them. I asked if I could get the EDGY (remember, the one before feisty fawn) package, also, but perhaps as I'm still new to Ubuntu, I hadn't figured out that the older version now means the current version as well.

2. It doesn't, I checked.You can tell me for days that it does, but if at the end of the day, my computer is still using indirect rendering, where does that get us? If you can help me enable that, tell me how. I searched on the forum but to no avail. In fact, most replies to questions about the open source ATI drivers are statements to the effect of, "Yeah, I can run Beryl/Compiz with it, but I can't use 3d acceleration for my games" over and over. And over.

---

### Post by whatever on 2007-04-20
fglrx 8.28 does not work with kernel 2.6.20.
if you want 3d acceleration with the "ati" driver make sure that xorg-driver-fglrx is uninstalled. if it's still not working post the content of /var/log/Xorg.0.log and the output of 'dmesg'.

---

### Post by botulismo on 2007-04-20
Okay, thank you. I'll try that and get back to you in a couple of minutes.

---

### Post by botulismo on 2007-04-20
It seems to be working properly now. Thank you, I really appreciate it.

---

