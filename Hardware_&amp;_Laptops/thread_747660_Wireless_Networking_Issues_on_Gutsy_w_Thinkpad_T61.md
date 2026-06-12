---
title: "Wireless Networking Issues on Gutsy w/ Thinkpad T61 &amp; IPW3945ABG"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by mattfredrikson on 2008-04-06
Hi,

I'm currently using Gutsy32 on a Thinkpad T61 with Intel 3945ABG wireless. When I first boot up, it works fine. However, if I leave it idle for a while then it drops the connection, and there is nothing that will bring it back. Additionally, if I take the wireless interface down and bring it back up intentionally, then it shows up in the list of active interfaces, but is no longer functional. Has anybody experienced something similar? Better yet: does anybody have suggestions?

---

### Post by sdennie on 2008-04-06
The default 3945ABG driver in Gutsy is very poor (the ipw3945 driver).  I would recommend moving to the iwl3945 driver (which is the default in Hardy).  I realize you have a ThinkPad but, the instructions from Dell should solve your problem: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

---

