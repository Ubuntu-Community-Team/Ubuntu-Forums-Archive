---
title: "What's the status of Optimus?"
date: 2013-08-04
forum: Hardware
---

### Post by PauloAugusto on 2013-08-04
I'm trying to choose a new laptop to purchase (including gaming) but almost all laptops come with Optimus.

About 1.5 years after launching Optimus, Linux was still unsuported - Nvidia's page **clearly** stated that if there were no BIOS option to disable the integrated Intel one, the Nvidia one would not work in Linux.
Then all the rumors and buzz about the newest Nvidia's Linux driver supporting Optimus in Linux.
However, just to confirm, I checked in Nvidia's page and they still **clearly** state the same - it won't work on Linux (with that exception that doesn't really matter since no recent laptops have it).

So, what's really the state of Optimus in Linux?
I absolutely can't find any authoritative answer to that...


I know about Bumblebee and Primusrun. What's the state about those also?
I have the idea (might be wrong, though) that I can make the OS use the Nvidia card on demand with Bumblebee but, with updates, I'll probably break it.

---

### Post by Yellow Pasque on 2013-08-04
Bumblebee works pretty well from the reports I've seen. As far as the "official" Optimus supports, it uses the nvidia card for everything, which isn't useful unless you're always hooked to AC or don't care about battery life. Seamlessly transitioning between the two GPU's based on load is still a pipe dream.

---

### Post by PauloAugusto on 2013-08-06
> **Temüjin said:**
> ... As far as the "official" Optimus supports, it uses the nvidia card for everything, ...
As in, it behave as if the Intel card/Optimus doesn't exist and uses always the Nvidia card? Are you pretty sure of that?

That would be quite awesome, I must say. I care little about Optimus - all I want is the gfx powers of the Nvidia card. I use my laptop as a (transportable) desktop, 99.9% of the time anchored to its "desktop" spot.

---

### Post by ElfenKiller on 2013-08-06
I don't think that's true. As far as I know, **bbswitch **([https://github.com/Bumblebee-Project/bbswitch](https://github.com/Bumblebee-Project/bbswitch)) can disable the nvidia card automatically if it's not needed.

---

### Post by oldfred on 2013-08-06
It is my understanding to use the new nVidia with limited Optimus support you need the newest kernel that will be in 13.10.

 NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)
Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)
Installing new nVidia driver 319.12 beta
[http://www.barunisystems.com/index.php/site/page?view=blog](http://www.barunisystems.com/index.php/site/page?view=blog)

---

### Post by grahammechanical on 2013-08-07
This might interest you. But then again it may not mean much.

[http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html)

Regards.

---

### Post by PauloAugusto on 2013-08-07
Bloody hell, what a freaking mess! How hard can it be to just «disable» the freaking integrated card!?
It almost makes me want to choose a desktop computer even though I don't have the space for it... Or go ATI, even though their Linux drivers are so much behind (well, at least their cards are usable, unlike Nvidia ones when behind Optimus - without ugly "hacking").

Thanks for all the replies.

---

### Post by Yellow Pasque on 2013-08-07
> How hard can it be to just «disable» the freaking integrated card!?
With Optimus, the integrated Intel always outputs to the screen, so it's never really disabled. It's more complicated than you think, and fighting between kernel devs and nvidia makes it more complicated than it has to be.

---

