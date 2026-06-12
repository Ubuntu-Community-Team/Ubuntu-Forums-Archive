---
title: "Program installs + internet."
date: 2008-12-17
forum: Hardware
---

### Post by lightspeed500oard on 2008-12-17
New to Ubuntu. I can't get any internet conectivity. Dell Inspiron 2200 Broadcom BCM4318 [Airforce One 54g] 802.11 is listed through Terminal. In hardware I find Dell Wireless 1370 Wlan-PC Card. Also tryed to install My Netgear USB Device but the CD wont intall, Msg...Cannot find the autorun program. In the internet connections I tryed to fill in the info but the OK button was grayed out and all I could do was close it down. Any sujestions would be great.

---

### Post by Ng Oon-Ee on 2008-12-17
It looks like you're trying to run the Windows setup CD. That won't work, obviously, as Ubuntu is a Linux distro, totally separate. Even if you can run the executables, they won't do what you expect or want.

Search for your specific model of WIFI card on these forums or online (add the word linux) and see if there's any HOWTOs. Most WIFI cards should work out of the box in your normal install.

---

### Post by xjcannonx on 2008-12-17
I believe your card is supported by bcm43xx-fwcutter so go to System--> Administration-->Synaptic package manager and look for b43-fwcutter and install that...

---

