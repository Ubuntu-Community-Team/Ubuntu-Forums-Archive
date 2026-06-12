---
title: "Can't find wireless device??"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by cassiuss on 2005-12-31
Hello,
New to Ubuntu - so far, it's great. BUT I'm running dual boot on a Dell Latitude 810 with built-in wireless, and would like to get the wireless card working. Ubuntu network config doesn't seem to see the card - what am I missing? I installed the basic system and added a few packages with apt. I seem to be missing something that lets Ubuntu recognize my built in adapter.

Any hints for me? THANKS.:confused:

---

### Post by Jeff12088 on 2005-12-31
It would be nice to know what model and type your wireless device is.
Check this list for more information on your card: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards)
If Ubuntu doesn't detect it, ndiswrapper might do the work.

---

### Post by Lambert on 2005-12-31
If nothing is in the list of the networking gui then you need a driver.

See if these links help

[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

If you have trouble with these then there are commands in the second link. You'll need to run the appropriate ones based on the step you're stuck on here so you can get more help.

---

### Post by cassiuss on 2006-01-01
It's a Dell Wireless 1350 WLAN Mini-PCI Card, Rev 4.4. Uses BCM4306/BCM2050 Chipset. THANKS.

---

### Post by Jeff12088 on 2006-01-01
According to the wiki link I provided, you need the official driver using ndiswrapper.
"ndiswrapper + bcmwl5a.inf"
"Truemobile 1350" in the link.

---

### Post by cassiuss on 2006-01-01
When I run ndiswrapper I get: 
================<paste>===========
cassius@barsoom:~$ sudo ndiswrapper -i bcmwl5a.inf
Installing bcmwl5a
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
cassius@barsoom:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5a invalid driver!
============ </paste> ===============

---

### Post by Jammy_Stuff on 2006-01-02
# Card: Dell Truemobile 1350 minipci 54mbps

    * Chipset: Broadcom Corporation BCM94306 802.11g (rev 03)
    * pciid: 14e4:4320
    * Driver: [http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE) (use bcmwl5a.inf in directory AR)
    * Other: So far, so good. WEP appears to work fine, as does WPA with CCMP/AES.

Make sure you are using that driver.

---

### Post by cassiuss on 2006-01-04
THANK YOU Jammy-Stuff. D'L'ed the driver you suggested, put it in /opt/var and loaded ndiswrapper. reboot and then network-admin can see the card. NOW I need to get back home and try it with my access point. (I use copper at work, wireless at home). THANKS TO ALL.

---

