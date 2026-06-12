---
title: "Noob needs ndiswrapper help - usb wireless netgear wn111"
date: 2010-02-13
forum: Hardware
---

### Post by Zorgoth on 2010-02-13
I have a 64-bit Windows 7 and a 64-bit Ubuntu karmic dual-booted and I want to use my usb wireless card and I think I need ndiswrapper to do it.  Unfortunately I don't know what to do to set something up with ndiswrapper and I can't understand any of the guides online.  I can't access the internet with linux until I get this card working or else buy a new one.  I am using a netgear wn111 usb wireless card.

---

### Post by IcarusR on 2010-02-14
Very straightforward HowTo here, read it & the linked pages through fully first.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

If you get stuck post exact problem here with details of wifi card ie chipset.

---

### Post by Zorgoth on 2010-02-14
I tried the guide and so far it hasn't worked.  I got wn111x (device is wn111 0846:9000) from the windows partition, but I don't have web.  The lights on the device don't flash like they do under windows and I don't see networks.  When I run ndisgtk I get a dialog with "Unable to see if hardware is present" and when I press "Configure Network" I get "could not find a network configuration tool."  The network configuration in the guide is outdated for Ubuntu 9.10 and I can't use it.  When I run ndiswrapper -l I get

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release
wn111x : driver installed
       device (0846:9000) present

EDIT: Although I get "unable to see if hardware is present" when i open ndisgtk, I get "Hardware present: Yes" once the program is started.

---

### Post by frankida on 2010-03-05
> **Zorgoth said:**
> I tried the guide and so far it hasn't worked.  I got wn111x (device is wn111 0846:9000) from the windows partition, but I don't have web.  The lights on the device don't flash like they do under windows and I don't see networks.  When I run ndisgtk I get a dialog with "Unable to see if hardware is present" and when I press "Configure Network" I get "could not find a network configuration tool."  The network configuration in the guide is outdated for Ubuntu 9.10 and I can't use it.  When I run ndiswrapper -l I get

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release
wn111x : driver installed
       device (0846:9000) present

EDIT: Although I get "unable to see if hardware is present" when i open ndisgtk, I get "Hardware present: Yes" once the program is started.

I had this problem too.

Goto System/Administration/Synaptic Package Manager/  

Search for Gnome Network Admin and install.

Worked for me!

---

