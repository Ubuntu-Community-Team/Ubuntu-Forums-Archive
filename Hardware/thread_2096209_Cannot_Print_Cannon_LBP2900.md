---
title: "Cannot Print Cannon LBP2900"
date: 2012-12-19
forum: Hardware
---

### Post by Sreeram Boyapati on 2012-12-19
OS : Ubuntu 12.10 64-bit
Printer : Canon LBP-2900
I have attached a URl image 
installed drivers 32 bit

problem : Cannot send data to printer its processing for a very long time

---

### Post by pdc on 2012-12-21
.......not sure which install method you followed .....

I enclose a screenshot of my printer properties.......it is quite different to yours ...........

32bit installs make life easier to run such printers if you are new to ubuntu ...

[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

from post #4, Sivella gives guidance ..

I prefer the 

> [COLOR="Blue"]ccp://localhost:59787 -[/COLOR]E option from here

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

........as one does NOT need the 

> [COLOR="Magenta"]sudo mkdir /var/ccpd[/COLOR]
[COLOR="SandyBrown"]sudo mkfifo /var/ccpd/fifo0[/COLOR]
[COLOR="Lime"]sudo mkdir /var/captmon[/COLOR] 

that 

> [COLOR="Blue"]ccp:/var/ccpd/fifo0 -E[/COLOR]  necessitates ........

---

