---
title: "Acer Aspire 3680 wireless solution"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by DirtyJay on 2007-10-18
Frustrated with getting your wireless to work?  Here is what I did.
Turn off laptop.  Flip upside down and remove back cover.  Unscrew original wireless card (Atheros AR5BXB6) and remove.  Order new Intel PRO/Wireless 3945ABG for $23 +$12freight, and install.  Reboot Ubuntu (Feisty Fawn 7.04) card became recognized.  

Ahhhhh.....feeling much better now!

In all fairness I am a new to ubuntu and struggled with getting through the guides for wireless.  So instead of pulling my hair out I looked for a card that seemed well supported or at the very least loads up without much work and I ordered it.  

Sometimes the best software solution is new hardware.(especially if it is cheap)

Good luck!

PS - If ordering a wireless card for your computer, pay attention to the TYPE of card you have.  Mine is a minipci express.

---

### Post by yelvington on 2007-11-03
A slightly less radical solution: Get a compatible PCMCIA wifi card, stick it in the side of the laptop, and live with it until the AR5BXB6 is supported, if ever.

I've wasted 20 or so hours trying to get the AR5BXB6 (which claims to be an  AR5006EG 802.11 b/g Wireless PCI Express Adapter Rev. 1 in "lspci") but it's just not happening, not with madwifi, not with ndiswrapper, not with anything I've tried. 

Much simpler to get a Trendnet from Compusa for $4 after rebate.

---

### Post by missiledave on 2008-02-24
this is how i got my wireless card (atheros 5006eg) to work without using ndis wrapper (inefficient anyways).

step by step madwifi install on gutsy for noobs.


First remove startup for linux-restricted-modules-common because it causes conflicts with the madwifi drivers.

run the following red commands from your terminal EXACTLY as they appear (hit enter after each line, do not run the commands together or they will not work)
```

sudo update-rc.d -f linux-restricted-modules-common remove
```



now its time to install the madwifi driver and required patch.

note:  you may need your install disc...


```
sudo apt-get install build-essential
```




download this package to get the madwifi patch [http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz)

unrar the madwifi snapshots into somewhere you can get to (i dont know if you need to keep it when you are done, but im not gonna delete it to find out.)


cd into the directory you unrared the madwifi  [eg] /home/missiledick/madwifi/madwifi-ng-r2756-20071018 [/eg]


```
patch -p0 < ../madwifi-ng-0933.ar2425.20071130.i386.patch\?format\=raw
```

```

make clean
```

```

make
```
```


sudo make install
```


then reboot your system and you should have wireless support without having to dick around with windose drivers and that crap.  

i didnt make this method up, i just found another version of it and cleaned it up and clarified it a little.  im just a new ubuntu guy trying to help other new ubutu peoples out.

my sound card was also an issue,  if you are having issues with realtek hd audio support let me know i found a super easy fix for that too.

---

