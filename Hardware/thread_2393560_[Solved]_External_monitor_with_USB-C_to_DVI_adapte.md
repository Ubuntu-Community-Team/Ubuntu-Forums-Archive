---
title: "[Solved] External monitor with USB-C to DVI adapter not working"
date: 2018-06-05
forum: Hardware
---

### Post by gugu88 on 2018-06-05
Hi everyone.


 I have a problem in connecting a second monitor.


 My laptop has only a HDMI plug and I need to use a DVI cable. To do so I bought a USB-C to DVI/VGA/HDMI/USB3 adapter.


 Unfortunately it does not work. If I plug a USB stick to the adapter this is immediately recognized (so I guess that the adapter itself works and my linux system “sees” it) but I tried with HDMI, VGA and DVI and with none of them it works. The laptop do not recognize at all any screen.  
 I tried the adapter with a windows computer and with a MacBook PRO and works just fine with both of them.  

 The adapter is [https://www.gearbest.com/cables-connectors/pp_1434948.html?wid=1433363&currency=EUR&vip=4265332&gclid=CjwKCAjw6djYBRB8EiwAoAF6ob7cn8Ne9TOYI8cD171LLxoaBqa8qTVu_gDoMH7_YbzDx2OF--KEQBoCs0cQAvD_BwE](https://www.gearbest.com/cables-connectors/pp_1434948.html?wid=1433363&currency=EUR&vip=4265332&gclid=CjwKCAjw6djYBRB8EiwAoAF6ob7cn8Ne9TOYI8cD171LLxoaBqa8qTVu_gDoMH7_YbzDx2OF--KEQBoCs0cQAvD_BwE)

 My laptop is a Tuxedo InfinityBook PRO.

 Running Ubuntu 16.04 (kernel 4.13.0-43-generic)


 Any help is appreciated.


 Thanks in advance

Guido

---

### Post by gugu88 on 2018-06-14
I solved the problem: in order to make the adapter work I had to go in the bios in Adavnced  Chipset Control and change the Display Digital Interface (DDI) control  from DDI to mDP (mini Display Port) to DDI to TBT (Thunderbolt). 
  Now, of course, if I would use the mDP I should switch back to DDI to mDP.

---

