---
title: "Setup HP Deskjet 2540 for wireless operation"
date: 2017-11-22
forum: Hardware
---

### Post by RayArdia on 2017-11-22
Ubuntu 16.04, latest hplip
I have tried for over a year to get my HP Deskjet 2540 to work wirelessly. I have read all post which purport to explain how to do it - all say that their method is foolproof but, although the printer works OK on USB cable I fail to get it to operate on wifi.
Can anyone point me to a DEFINITIVE set of instructions?

---

### Post by ajgreeny on 2017-11-22
[LIST=1]
[*]Make sure you have **hplip** and **hplip-gui** installed on your machine as that may be the best way to install a printer by going to the + icon in the hplip-toolbox toolbar.
[*]Now choose** Network/Ethernet/Wireless network (direct connection or JetDirect** in that window as shown in my first screenshot. 
[*]Second you need to click on the **Show Advanced Options** also shown in the screenshot and select the **Manual Discovery** tickbox where you enter the IP of the printer which you can probably find from the printer screen itself, if it has one, or your router setup **Attached Devices** page; it will probably be something similar to 192.168.1.10 but the final two digits can be anything up to 256.
[*]Now click Next and hplip should find the printer for you and allow you to name it appropriately.
[/LIST]

---

### Post by Autodave on 2018-09-05
Also, have you enabled wireless in the printer setup screen? (Done on the printer.)

---

