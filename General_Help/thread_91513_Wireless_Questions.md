---
title: "Wireless Questions"
date: 2005-11-17
forum: General Help
---

### Post by sfagundes on 2005-11-17
I have Ubuntu Breezy running on my HP dv4165 notebook.  My Intel Pro Wireless card is seen as eth0.  It works fine, but the question I have is there a way to have the wireless automaticcaly connect at bootup?  As it is now, I have to type "sudo ifup eth0" every time i reboot or log off?  Also is there a way to store multiple wireless profiles for example 1 set with a certain ssid and key, and another set that's different?

Thanks

---

### Post by Dr. Nick on 2005-11-17
not sure on the sudo ifup part but for profiles check out wifi-radar , network manager, or you can try to use the network control panel and make a new location

---

### Post by soulestream on 2005-11-17
put your wireless info for the one you want to connect at startup in /etc/net/interfaces.


soule

---

### Post by Yoda_Oz on 2005-11-17
i just did it with the gnome network gui control panel thingie.

system/administration/networking!

boots up everytime without fail.

HOPE THIS HELPS...

---

