---
title: "Udev rule dont work"
date: 2015-10-22
forum: Hardware
---

### Post by Luca_Brasi on 2015-10-22
Hello to everybody! I created udev rule but it dont work. I want do some action when i add/remove USB mouse. 
This is my current rule, which i put in /etc/udev/rules.d/95-touchpadDis.rules
```
ACTION=="add", ATTR{product}=="USB Mouse", ATTR{manufacturer}=="A4Tech", RUN+="/usr/bin/xinput --disable 13"
ACTION=="remove", ATTR{product}=="USB Mouse", ATTR{manufacturer}=="A4Tech", RUN+="/usr/bin/xinput --enable 13"
```

P.S. I tried to use different attr (idVendor, idProduct) but that was not succesfully

---

