---
title: "Nvidia -PLEASE HELP!!!"
date: 2008-09-12
forum: General Help
---

### Post by spicanhellhammer on 2008-09-12
hello everyone, I'm not really new to Linux, but I have been trying to get an Nvidia card to run unsuccesfully and it's becoming really frustrating. I have installed and uninstalled the drivers several times using different methods, including manual install with kernel module compilation and everything, and the latest EnvyNG, with two different cards, both verified in the list of supported nvidia cards, and I always get the same error, the system crashes on start up during the splash screen when I try to boot with the Nvidia graphics card, and if I use safe mode, it gives me an error visible in console mode saying that:
init: rcS main process (2640) killed by SEGV signal
init: unable to execute '/bin/sh' for rc-default: no such file or directory
init: rc-default main process (3976) terminated with status 255

I replaced /bin/sh file (wich was a shortcut to: /bin/dash) with /bin/dash and changed the name to /bin/sh, and I got the same problem but only with this message:

init: rc-default main process (3979) killed by SEGV signal

I have to switch back to on board graphics if I want to use my pc. I have really tried for hours and hours and I think I'm gonna strangle someone to blow off some steam.
I've tried this with ubuntu Fiesty, Comfusion and currently with Hardy, I know for a fact that these cards work, I just can't seem to pull it off who knows why, and on top of this, my integrated video became really defficient and will not go back to normal.
my sistem is:
Intel® Desktop Board D946GZIS
NVIDIA GeForce 7100 GS pci express 256mb and/or a 6 series turbo cache 128 mb with a dual core 3.0ghz 32 bit processor

besides this, everything works great with ubuntu, but as a man, this issue is hurting my pride, putting a side the fact that I can't take full advantage of my graphics accelerator.

If anyone could help me, I would be thankful for life and would do anything I could to return the favor.

---

### Post by JECHO on 2008-09-12
> **spicanhellhammer said:**
> hello everyone, I'm not really new to Linux, but I have been trying to get an Nvidia card to run unsuccesfully and it's becoming really frustrating. I have installed and uninstalled the drivers several times using different methods, including manual install with kernel module compilation and everything, and the latest EnvyNG, with two different cards, both verified in the list of supported nvidia cards, and I always get the same error, the system crashes on start up during the splash screen when I try to boot with the Nvidia graphics card, and if I use safe mode, it gives me an error visible in console mode saying that:
init: rcS main process (2640) killed by SEGV signal
init: unable to execute '/bin/sh' for rc-default: no such file or directory
init: rc-default main process (3976) terminated with status 255

I replaced /bin/sh file (wich was a shortcut to: /bin/dash) with /bin/dash and changed the name to /bin/sh, and I got the same problem but only with this message:

init: rc-default main process (3979) killed by SEGV signal

I have to switch back to on board graphics if I want to use my pc. I have really tried for hours and hours and I think I'm gonna strangle someone to blow off some steam.
I've tried this with ubuntu Fiesty, Comfusion and currently with Hardy, I know for a fact that these cards work, I just can't seem to pull it off who knows why, and on top of this, my integrated video became really defficient and will not go back to normal.
my sistem is:
Intel® Desktop Board D946GZIS
NVIDIA GeForce 7100 GS pci express 256mb and/or a 6 series turbo cache 128 mb with a dual core 3.0ghz 32 bit processor

besides this, everything works great with ubuntu, but as a man, this issue is hurting my pride, putting a side the fact that I can't take full advantage of my graphics accelerator.

If anyone could help me, I would be thankful for life and would do anything I could to return the favor.

maybe you have already tried this but in the past ive had a similar problem and this fixed it:

instead of using envy and all of that stuff go directly to nvidias website and download  the most recent driver for your card. then boot into terminal and install it. then restart.

hopefully that works...


...if it doesnt and youre out of options i suggest doing a clean install and trying what i said above again. THAT should work no matter what.

---

### Post by Joeb454 on 2008-09-12
Moved to General Help

---

