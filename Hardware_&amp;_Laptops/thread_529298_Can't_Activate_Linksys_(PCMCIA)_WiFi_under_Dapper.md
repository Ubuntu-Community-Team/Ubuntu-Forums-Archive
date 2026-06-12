---
title: "Can't Activate Linksys (PCMCIA) WiFi under Dapper"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by IainB on 2007-08-19
I am a new user to Ubuntu. I have loaded 6.06 LTS (Dapper) and updated. 
I have a Linksys PCMCIA WiFi Card, WPC54G ver. 1.2.

Under Networking, the WiFi card is displayed as eth1, "not active".
Initially I tried simply activating it, having reset my WiFi router to not use WEP, no SSID broadcast. I entered the SSID and "activated". It reported as active, but I could not ping the router or access the Internet. After a reboot, the WiFi interface again shows as "not active".

I installed ndiswrapper and downloaded the GUI. I downloaded the Windows (ver 1.0) driver from Linksys, and then installed the driver using the Linksys provided ".inf" file. The GUI reported the device as present. I then deactivated eth0 (Cat5), and then Activated eth1 (WiFi), checked the settings. Still no access, and again after reboot the device shows as "not active".

Iain B.

---

