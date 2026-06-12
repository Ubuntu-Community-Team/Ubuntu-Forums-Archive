---
title: "Need help with MSI P6NGM motherboard"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by ownage88 on 2008-03-11
Hy!!
I've got a nother pc with MSI P6NGM motherboard.I was installed Ubuntu 7.10 and all work fine except the sound and the integrated graphic card.The sound card doesn't matters but the graphic card yes,and when i'm trying to install it,it can't.plz help,or give me advice how to install it :confused::confused:.Sorry for my noobish English:)
 
THX

---

### Post by teaker1s on 2008-03-12
You need to find out the graphic's chip make from motherboard spec 

From a review I think it's
GeForce 7000 series graphics core, if you can get terminal but no gui
try
```
sudo dpkg-reconfigure xserver-xorg
``` a graphic screen will appear.
You will need to select either nv or vesa as a trial- if neither work you will need linux driver from nvidia.

---

