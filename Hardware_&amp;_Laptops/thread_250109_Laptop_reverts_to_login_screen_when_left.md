---
title: "Laptop reverts to login screen when left"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by Maverick321 on 2006-09-03
My HP pavilion zd8000 reverts to the login screen when it is left running by it self.  

It seems like it only happens when i am running XGL/compiz, but it doesnt happen at regular times.  I can find any error messages in the logs that jump out and say why this is whats happening.  

It doesnt happen very often, ran all last night for about 14 hours then when I started burning a data DVD and went outside, by the time i came back in about 5-10 mins it was sitting on the login screen.

There is one message in Xorg.93.log

```
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
```

The drmOpenDevice messages repeat with increasing card number to about 250. Is this a problem?

Has anyone else experienced this? Or does anyone know were to look for what might be causeing this problem.

---

