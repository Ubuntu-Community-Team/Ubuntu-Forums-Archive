---
title: "Display driver for UniChrom II IGP on 9.1"
date: 2009-11-09
forum: Hardware
---

### Post by chemical349 on 2009-11-09
anyone expert can help? 
i am a newbie to ubuntu/ linux.

my netbook is using via v7 cpu with integrated display card.

the model is unichrom pro ii IGP 

when i try to install 9.04, i can get a 80% of the screen. 
the tool bar on the top of the screen, i can get from the "Application" button to the "Network", depends on resolution i select, some to "Envelop" button. when i connect my netbook with an external monitor, i can get the full screen no matter what resolution i select. (but without the mouse pointer) 

i think this is the driver problems.

when i try to install 9.1, the whole screen is just keep flashing.

anyone could help me??? 
i can find some driver from the manufacture
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
Because i am to green, i dont know how to even try to try these driver on my machine. can anyone shred me some light????????

also, i will need a wifi driver, can someone tell me how to install a wifi driver???

million thanks in advance.

---

### Post by Yellow Pasque on 2009-11-09
> also, i will need a wifi driver, can someone tell me how to install a wifi driver???

Use one of the following commands to figure out what chipset your wireless card has and whether there's a driver currently loaded for it:
```
sudo lspci -vv
sudo lshw -C network
```
Search by the name of the chipset.

---

