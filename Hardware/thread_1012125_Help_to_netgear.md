---
title: "Help to netgear"
date: 2008-12-15
forum: Hardware
---

### Post by Chriff on 2008-12-15
Heey, Im a new Ubuntu user, but I got a relly big problem!? :cry:

I installed Ubuntu to make my laptop faster, and it work jubii


but the problem is :

I can't get on the internet cuz I can get my netcard (Netgear PC Card WG511 v2 (China) ) to work :cry:   If anyone can tell me where I can get a driver or something there can make my netcard working I will be very great full! 

PLZ HELP! 

best regards Chriff (;

---

### Post by elvinatom on 2008-12-15
check out this page:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by rbo1212 on 2009-01-17
You'll need an internet connection.

Go to Synaptic Package Manager and install ndisgtk, ndiswrapper-common and ndiswrapper-utils-1.9

After installing go to System Administration and start Windows Wireless Drivers

When it asks for the driver use the Windows XP inf file (I have tried to attach it to this reply, but don't know if it will show up when I post it.

The card should come to life immediately when the install finishes.

This is the .inf file from the installation disk that came with the card. I'm using the wireless card to post this reply.

Best of luck, I hope the .inf file posts.

---

