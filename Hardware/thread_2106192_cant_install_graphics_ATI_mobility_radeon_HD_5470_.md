---
title: "cant install graphics ATI mobility radeon HD 5470 / sony vaio"
date: 2013-01-18
forum: Hardware
---

### Post by elmou on 2013-01-18
hello guys i just installed "**ubuntu 12.10**" on my laptop and i got stuck at installing ATI driver ,i'm not an advanced user
i have ati **ATI mobility radeon HD 5470**
i downloaded :
[B]amd-driver-installer-catalyst-13.1-linux-x86.x86_64
amd-driver-installer-catalyst-12.10-x86.x86_64
amd-driver-installer-12.6-legacy-x86.x86_64[/B]
from the amd websites 
i unziped them and sh ... run them and a "error message" pop up

i search it on google and i ending crashing my system :(
plz guys help

---

### Post by maidomax on 2013-01-18
I would like to know this too...

---

### Post by wilson99 on 2013-01-19
You're not going to have luck... for now...

I have a DV6 3020EP and for now, there isn't support for this graphic...

Hope someone can help us! ;)

---

### Post by Mark Phelps on 2013-01-20
AMD is NOT the ATI of years ago who actively support Linux driver development -- see below:

[http://www.muktware.com/4768/amd-shuts-down-operating-systems-research-center-dismisses-linux-employees]("http://www.muktware.com/4768/amd-shuts-down-operating-systems-research-center-dismisses-linux-employees")

---

### Post by maidomax on 2013-01-21
I managed to install the drivers on my laptop, although I must admit that I don't see any difference in the quality of my graphics.  

[LIST]
[*]First of all download and unpack the latest drivers, (for me it is "**amd-driver-installer-catalyst-13.1-linux-x86.x86_64"** and I see you already have that one)
[*]Then run **chmod +x amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run**
[*]After that, you will be able to run the installer with **sudo ./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run**
[*]Follow the installer prompts, and after a few tweaks and restarts you will be all setup
[/LIST]
Note that you will adjust your display propertis in the Catalyst admin panel, not the usual way. I had some problems figuring it out and getting it to work, but in the end I did, and I don't think it's that complicated, so I won't get into the details here. 

Once again, I see no improvement regarding performance, but I still haven't tried to install and play games.


I hope this works for you too.

---

### Post by Mark Phelps on 2013-01-21
> **maidomax said:**
> ...Once again, I see no improvement regarding performance, but I still haven't tried to install and play games...

That mirrors my experience with AMD HD 4290 graphics chipset.

Years ago, first thing I did after an Ubuntu version install was download and install the fglrx drivers -- because those were the only way I could get multi monitors (of different sizes) to work and get decent graphics performance.

But, after the Ubuntu 11.04 version, the open source Radeon drivers got better and better.

I tried both Radeon and fglrx drivers with 12.04 -- and like you, saw no improvement in performance of the fglrx drivers.

---

### Post by maidomax on 2013-01-25
Annoyingly, when ever I restart my computer, the resolution setting for my right monitor gets reverted and I need to set it each time... I haven't had this problem before I installed the drivers, and the drivers didn't enhance my GPU performance in any visible way. I'm pretty sure that I will uninstall them considering....  :mad:

---

