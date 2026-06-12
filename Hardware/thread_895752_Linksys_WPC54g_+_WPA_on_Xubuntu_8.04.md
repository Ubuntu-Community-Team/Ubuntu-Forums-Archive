---
title: "Linksys WPC54g + WPA on Xubuntu 8.04"
date: 2008-08-20
forum: Hardware
---

### Post by lepreshawn on 2008-08-20
Cannot make my Linksys PCMCIA WPC54g run WPA on XUBUNTU (8.04). I have seen quite some threads about this (usually old ones, 2006, 2005).

In these threads people were strugling, installing wpa_supplicant, etc.

In Xubuntu, all seems OK, wpa_supplicant is in place. But on the network-manager application, when editing the wireless network settings, there is no option to activate WPA, only WEP.

Does anybody here have such a card running WPA on Xubuntu 8.04? What is the trick.

Thanks in advance for you help.

---

### Post by Venlaar on 2008-09-05
I am having a similar issue. I have a Linksys WPC54G ver5 card using the Marvell chipset. I installed the latest drivers from [http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230040888B432&displaypage=download#versiondetail]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230040888B432&displaypage=download#versiondetail")
using ndiswrapper. After doing modprobe ndiswrapper and rebooting the lights on the card came on and network manager saw several wireless networks. I tried to connect to my WPA TKIP network but it would just come back and ask me for the password again each time. I then tried to connect to an unsecured open network the card was seeing but it wouldn't connect to that either.

---

