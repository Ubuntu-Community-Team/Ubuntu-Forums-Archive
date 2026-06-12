---
title: "problem with HP wireless button / switch"
date: 2008-04-30
forum: Hardware
---

### Post by orkid on 2008-04-30
I have problem with additional button on HP notebook (6715s). The button turns on/off wireless network. I have installed ndiswrapper for Broadcom WIFI card and the WIFI works correctly. However if network is turned off using the button before I boot Ubuntu, the system do not see WIFI card and button do not react. When I turn on the card in Windows and return to Ubuntu everything works correctly. In the case when I press button WIFI led is turn on and off. However without using Windows I'm unable to turn WIFI card on for the first time. Does anybody have any idea how to diagnose the problem? It this wireless button is treated as another input device in Ubuntu ?

---

### Post by evas80 on 2009-02-25
The following solution worked for me. After logging into ubuntu, turn on the Wireless Switch then restart the Network Manager with the following command

sudo /etc/init.d/NetworkManager restart

then right click on the Network Manager applet and verify if the "Enable Wireless" is enabled/checked.
 
Might need to refresh/restart network connection as well. 

sudo /etc/init.d/networking restart

Let me know if this works.

---

