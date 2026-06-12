---
title: "Unable to start xorg"
date: 2010-12-21
forum: Hardware
---

### Post by Bananasdoom on 2010-12-21
I am running Ubuntu 10.10, Card: Nvidia Vanta. I have removed the Nvidia drivers because they did not load xorg when I booted after I enable the proprietary drivers so I now I had to remove them. I cant start xorg, When I try to start x org with ```
sudo startx
``` I get a message ```
No screens found
```. How do Install the drivers purely from the terminal I know I need the proprietary Nividia drivers "71.86.xx". If this is not possible please tell me how to use my on mainboard's graphics because even when I remove the card I cant get into the GUI.  

Please Help Me Ubuntu Community Your My Only Hope

---

### Post by Bananasdoom on 2010-12-21
anyone?

---

### Post by hellnest on 2010-12-21
What Nvidia card you use? try ths from terminal. Must connected to the internet

$ sudo apt-cache search yourdrivernamehere
$ sudo apt-get install thenameyoufoundinthefirstcommand

I hope it's help, don't be affraid when you must face a command line... :)

---

### Post by Bananasdoom on 2010-12-21
I am not sure what the card is because It came bundled with a motherboard but it has a nvidia vanta chip that uses the 71.86.xx driver set I think what would be my "yourdrivernamehere" ? for this chip

---

### Post by Bananasdoom on 2010-12-22
Bump

---

### Post by sikander3786 on 2010-12-22
Try,

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Note, capital 'X' for X11.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

Please let us know how that goes.

---

### Post by Bananasdoom on 2010-12-22
sikander3786 

THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK  YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU   THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK  YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU   THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK  YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU   THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK YOU  THANK  YOU  THANK YOU  THANK YOU  THANK YOU  

:grin::grin::grin::grin::grin::grin::D:D

It worked Thanks

---

