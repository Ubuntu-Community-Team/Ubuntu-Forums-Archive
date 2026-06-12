---
title: "Acer AL2216WBD 22in Wide Screen"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by Cullen on 2008-02-01
I recently swapped my old CRT monitor for an Acer AL2216WBD 22in Wide Screen, how do I tell Ubuntu that I've changed displays?

I have tried
sudo dpkg-reconfigure xserver

and it ran me through a wizard, I plugged in the hoz and vert fequency ranges and selected the available resolutions as provided by the owners manual, but I am still unable to get true wide screen support. Any suggestions?

---

### Post by taurus on 2008-02-01
Try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, you can restart X server with <Ctrl><Alt>Backspace.  What graphic card do you have?

---

