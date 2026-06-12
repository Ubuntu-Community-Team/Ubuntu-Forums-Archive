---
title: "serial console access to cisco routers"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by anu2505 on 2006-06-09
I have Ubuntu 6.06 installed on IBM thinkpad T22.
I am unable to access cisco router console through the laptop serial port.
I have tried minicom with /dev/ttyS0 set for 9600 8N1 and also tried gtkterm as suggested by some other posts in this forum.
Please advise what else needs to be done to get this to work.
Device manager and dmesg output list /dev/ttyS0 as the serial port available.

---

### Post by khughes on 2006-06-09
Everything that you have done in minicom is correct so far but there is one more essential thing you must do to make it work with routers,switches, etc....

Open minicom, hit Ctrl-a to bring up the bar at the bottom, then hit Z. This should bring up a menu where you then need to hit O for "configure minicom". This will bring up another menu where you will see "modem and dialing". Use your arrows to navigate to that. On the next page, you need to erase everything on the line called Init string. Try that, if it doesnt work then type the word "clear" without quotes on the init string line. Then just reinitialize the modem or close and reopen the program and hit enter a couple times while being hooked up to a router. You should see the prompt.

---

