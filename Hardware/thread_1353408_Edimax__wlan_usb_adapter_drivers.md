---
title: "Edimax  wlan usb adapter drivers"
date: 2009-12-12
forum: Hardware
---

### Post by alfo982 on 2009-12-12
Hi everybody, I've just bought a wlan usb adapter: **Wireless nLite mini-size USB Adapter** **(EW-7711UMn)**, and I would install the drivers in my UBUNTU 9.10.

I would use the windows drivers with ndiswrapper, but inside of the CD there is no trace of .inf file!!!
I try to find it in internet but only a zip pack is available... and inside no .inf file
Is it possible? and if yes, what could I do?

---

### Post by alfo982 on 2009-12-13
Just to give an help to the community of UBUNTU... I "solved" this issue downgrading to the Jaunty version!

I've not found nothing better...

---

### Post by jezsoadam on 2009-12-21
Install the **linux-backports-modules-karmic** package, it works for me. I'm using the same wireless stick.

---

### Post by evlev on 2010-08-04
I know this is old, but this is the first result on google for "ew-7711umn ubuntu",so I hope this helps someone:

For Karmic and Lucid, add the line "blacklist rt2800usb" 
to /etc/modprobe.d/blacklist.conf and reboot

since this is an administrative task, use something like:
sudo gedit /etc/modprobe.d/blacklist.conf
to edit the file

the solution comes from this page: 
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax")

I have no idea what it does, my guess is it resolves some kind of driver clash, anyway it works for me

---

