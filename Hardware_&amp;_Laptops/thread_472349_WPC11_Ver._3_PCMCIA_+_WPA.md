---
title: "WPC11 Ver. 3 PCMCIA + WPA"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by bbarcelo on 2007-06-12
I've happily been running Ubuntu on one of my file servers for a while now without issue and am very pleased with all of it. Now I've decided to add it to one of my laptops. This laptop had trouble using a Linksys WPC11 Ver. 3 in Windows and I figured the solution to all the blue-screening would be a nice, clean Ubuntu install. I had Ubuntu auto-install itself and everything is detected and working fine except the card. I can't say for sure the card isn't actually being detected though as I don't really know of a way to check this as I would in Windows, so that's question number 1.

I also was unsure whether or not I had ever upgraded the firmware of the WPC11 and want to, but I can't find a flash utility that will update the Linksys WPC11 Ver. 3 to be WPA compatible. That's question number 2.

I will surely post some more on this after I've gotten these first two things resolved. Thanks for any help.

---

### Post by jml on 2007-06-13
According to this link,

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

 your card is supported.  But you may not be able to configure WPA encryption.

Since your card is designed to support the 802.11b protocol, it will not support WPA encryption out of the box.  I do not know if there are any firmware upgrades that will allow this hardware to support WPA encryption in Linux.

If WPA encryption is important to you, (it is for me,) you may want to buy an 802.11g compatible card with a chip set that is supported by Linux, (like the Atheros chip set,) and also supports WPA encryption.  The two cards that I have used successfully are the NetGear WG511T, and the Cisco Aironet 802.11 a/b/g wireless card.  ope this is of help.

Joe

---

### Post by bbarcelo on 2007-06-13
[This link]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859958334&packedargs=sku%3D1115416828350&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5833445678B07&displaypage=download#versiondetail") shows the available driver downloads from the Linksys website. You can clearly see there is a driver that supports WPA in Windows, but I'm guessing this driver download also flashes the firmware and then is just an updated driver to make use of the new security features. I'm just trying to get the firmware flashed for now and then see if Ubuntu will just auto-recognize it or something. I'm just looking for some insight on what I should do here. I'm not going to buy another card, so that's out because I just don't have the money.

---

