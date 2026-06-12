---
title: "ATI Radeon 9200 PRO - Drivers... Need help."
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by PROject-Emerald on 2009-06-09
Hey... I'm kinda new to Ubuntu, and I need some help.

On Windows, I can run CSS at ~50FPS. On Ubuntu, same card, I can only get 5-7 FPS which is unplayable.

I know with WINE it's going to be slower, and I know it's because as of now I'm using default/generic drivers, not specialized ones.

ATI/AMD's support for my card is garbage, so are there any alternatives to get my card running at the capacity it's supposed to?

ANY help would be great.

Also, i did LSPCI |grep ATI and got this:

```
mike@mike-desktop:~$ lspci |grep ATI
01:05.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:05.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
```

My box for my card says it's a Radeon 9250, but this is telling me otherwise.
(It's a Diamond Stealth Radeon 9250, I guess.)

---

### Post by Mark Phelps on 2009-06-09
In terms of drivers, no. The current open source is all that is available under Ubuntu 9.04.

If you do "man radeon" in a terminal, you will see the list of options available for the radeon open source driver.  You would have to experiment with those to see what improvements you might get.

Another source of information is the Phoronix forums. They do a lot of tweaking with the ATI drivers.

---

### Post by darklordzim on 2009-06-11
im having exactly the same issue, with my card i get a display, but then after awhile my screen stops rendering correctly.... i've been trying to surf for a way to at least even getting it working to a point i can stand especially if i start opening more than one app. and when i just do "driver "radeon" the computer wont even boot into X

---

