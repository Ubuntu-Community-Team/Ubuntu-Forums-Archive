---
title: "Wifi broke after update"
date: 2010-05-07
forum: Hardware
---

### Post by bisconer on 2010-05-07
Ok i have a Linksys USB wifi Adapter (model number WUSB600Nv2), using this [link]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N") i was able to install the driver and had no issues with it running on Ubuntu 10.04.

So i get home, and see there are updates ready to install, after installing and rebooting my computer the device is no longer showing up in either the connection button on the panel or via ifconifg.  The light on the device is no longer turning on either. However, lsusb still shows it to be there.

EDIT: I have even tried to recompile the driver, as if i never installed it, and it still doesn't work.

---

### Post by tmaxx on 2010-05-08
Exact same problem. Found that there are updates in the Update manager. Performed an updated followed by restart few minutes ago. The Wifi has stopped working since then. It attempts connecting for around 5 -10 minutes and then brings up the connection name / Password window. 

Not sure how to progress from here.

Any help would be greatly appreciated. 

TMAXX

---

### Post by bisconer on 2010-05-08
I have confirmed it to be an update issue, after creating a usb drive install, i installed the driver to get wifi, then ran the update to the kernel.  After installing/restarting from the updates, the wifi was no longer working.  I removed the old drivers, and recompiled and still dose not work.

Any help on this would be greatly appreciated as this is my only way of connecting to the Internet.

---

### Post by abdusamed on 2010-06-14
GOIGN TO KEEP IT SUPER SIMPLE..i can create UNSECURED network on ubuntu and share it. vista detects it and works!! but if i create either in vista machine or ubuntu machine a wireless which is secured with any type of encryption..NONE of the machine seems to connect to it though they detect a secured network. Vista keeps on saying that the key enter is invalid and on ubuntu machine.. trying to connect to vista secured network.. ubuntu doesn't do anything!!! WHAT UP WITH IT!

---

