---
title: "Switch wireless on/off by keyboard?"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by levis on 2007-09-14
How can we switch the wireless on/off using the default hot key on the keyboard? I can use it in windows but it didn't work in ubuntu 7.04. Thanks!

---

### Post by levis on 2007-09-14
Help me, i can use the Fn key with all other function but not Fn+F2 to turn on/off wireless

---

### Post by tgalati4 on 2007-09-14
You could define a hot key (any key really) to run a script called shutdownmywirelessnow.sh

Inside the script:

#!/bin/bash
#My super cheesy script to shut down my wireless.
sudo ifconfig wlan0 down

---

