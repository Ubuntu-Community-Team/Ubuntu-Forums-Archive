---
title: "broadcom woes - bcm4318"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by shadowplane676 on 2007-08-30
ok, first off, i HAVE tried the how-to about 15 times, this is something more than that i believe at this point.

i started by installing feisty on my zv6000 laptop and actually got the how-to to work and had wireless working.....until i tried to get bery to work on my ATI Xpress 200M and broke my install. ever since then i CANNOT get my wireless to work at all. the how-to installer dies on me every time. i DO have the python gtk-2 installed so i can run the script. BUT i get this on running it - installer says incompatible chipset and recommends ndiswrapper (the first time when it DID work, it recommended firmware....*shrug*). i go with recomendation and the null output is:

> 
X error: BadDevice, invalid or uninitialized input device 167
  major opcode:  144
  minor opcode:  3
  resource id:  0x0
failed to open device
X error: BadDevice, invalid or uninitialized input device 167
  major opcode:  144
  minor opcode:  3
  resource id:  0x0
failed to open device
Xlib: connectien to ":0.0" refused by server
Xlib: no protocol specified

error: can't open display: :0.0
press CTRL+C to close this window


shell output is

> stuart@Takahashi:~/bcm43xx-gtk-installer-0.3.1$ sudo python installer.py
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
./wcm.sh wifi-radar
kdesu './bcm43xx-ndiswrapper.sh'
stuart@Takahashi:~/bcm43xx-gtk-installer-0.3.1$    

i cant figure out why this wont work again and some help would be most appreciative

---

### Post by MatthewAPeters on 2007-09-02
I have an hp zv6000 as well - but my research has shown that our ATI radeon Xpress 200M cards are incapable of open GL (either a "known bug" or intentionally "neutered" chip - don't know which).  I was unable to get Beryl working, and ended up dropping it.  I am using the Broadcom wireless with ndiswrapper succesfully on Ubunty 7.04 (Feisty).  

This bit of your output looks like you are having an x term problem:

failed to open device
Xlib: connectien to ":0.0" refused by server
Xlib: no protocol specified

perhaps if you loose Beryl (it is obsolete in Feisty, anyway - Compiz Fusion absorbed it - but I haven't tried Fusion on zv6000) you can get past the Xlib error?

Good luck!

---

### Post by shadowplane676 on 2007-09-02
ok, well after i messed with beryl, i have formatted and reinstalled Feisty about 5-6 times so far and i still get that device error and the crapping out on the wireless....

---

