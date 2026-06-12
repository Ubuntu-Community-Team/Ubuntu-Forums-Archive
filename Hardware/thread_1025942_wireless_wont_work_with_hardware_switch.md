---
title: "wireless wont work with hardware switch"
date: 2008-12-30
forum: Hardware
---

### Post by yon2501 on 2008-12-30
My cousins acer extensa 4420 has a wireless switch on the front but for some reason by default ubuntu does not recognize the wireless card in the pc, is there a special driver for hardware wireless switches or for acers in general. id have to download it on her windows partition and copy it over.

---

### Post by teaker1s on 2008-12-30
it is possibly missing keycodes  run 
```
xev
``` in terminal and see if you can see activity when switching
**Example**
The wifi kill switch uses  keycodes (use in /etc/rc.local):

/usr/bin/setkeycodes e055 159
/usr/bin/setkeycodes e056 158

```
sudo chmod a+x /etc/rc.local  
```

---

### Post by yon2501 on 2008-12-30
that didnt seem to work any other ideas anyone?

---

### Post by tornadof3 on 2008-12-31
Try installing the "madwifi" and "ndiswrapper" packages from the Synaptic Package Manager. Doing this has always allowed the wireless to appear when I then go to System -> Admin -> Hardware Drivers.

May help you.

---

