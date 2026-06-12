---
title: "Wireless card issues"
date: 2009-08-09
forum: Hardware
---

### Post by J_Sas on 2009-08-09
Okay, finally got ubuntu installed.  Never was able to get it directly installed from the HD, so I had to finally burn it to a disc, and that worked beautifully and much easier.

Now, it looks like EVERYTHING is working on the system with my laptop, except for my wireless card.  

Laptop is a Compaq Presario V2000, uses a PCI card Broadcom BCM4318 (Airforce One 54g), using driver BCMWL5.SYS

I looked into Ndiswrapper, but have no idea how to get this to work. It looks like my card will work with it, but I'm still not clear on everything ubuntu/linux. 

What should I do at this point?  Is there an easier solution if I plug my laptop directly into my router and download something?

Thanks for your help!
J

---

### Post by arky on 2009-08-09
I suspect that your card doesn't work well with NetworkManager. The driver is already present in the kernel. You can use iwconfig commandline program to connect to internet or use other network tools like wicd and wifi-radar

---

### Post by J_Sas on 2009-08-09
Why would the card not work well?  It is listed as compatible with ubuntu, and included as an accessible driver in ndiswrapper.

I'll check out these other options...
J

---

### Post by Johanano on 2009-08-09
Have you run jockey-gtk? (don't know what it's called in the menu, but it might be "hardware drivers" or something along those lines. Otherwise just run it from a terminal).

---

### Post by arky on 2009-08-09
Filed a bug report here. 

[https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/410963](https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/410963)

Please add more information to that bug report.

---

### Post by sergiom99 on 2009-08-09
Hi. I have a similar card, BCM4328 and it works out of the box since Hardy. No need for ndiswrapper and Window$ INF files.
Newer kernels already have support for Broadcom chipsets.

Just do a:
```
sudo apt-get update && sudo apt-get upgrade
```
to update your system. Reboot. Then go System > Administration > Hardware Drivers and check "Broadcom STA Wireless Driver."
Check for a detailed explanation: [http://ubuntuforums.org/showthread.php?t=870575](http://ubuntuforums.org/showthread.php?t=870575)

Also, Network Manager has been reported some times as "broken", especially when connecting to WPA and WPA2 encrypted networks. Give Wicd a try, its awesome and it works smoothly with BCM drivers.
```
 sudo apt-get install wicd
```

Good luck!

---

### Post by J_Sas on 2009-08-09
Actually, nothing shows up in the Hardware Drivers section.  I was suprised.  Expected to see at least the NIC and other common hardware on the computer.  

I will try the steps you suggested, sergiom, and let you know how it goes.

THanks!
J

---

### Post by J_Sas on 2009-08-09
SUCCESS!

Your suggestion worked... all ubuntu needed was to be updated and upgraded... I suppose I would have found this out automatically if I had my ethernet port plugged in and access to the internet.  It never occurred to me that it would need it since it was the latest version.

I did go ahead and install wicd at the same time, and you're right, it's quite a bit easier to use and more familiar GUI.  However, it took me a few seconds to figure out how to configure my connection with the WPA password. 

Good to go! Thanks for your help!
J

---

### Post by sergiom99 on 2009-08-09
Glad you made it.
Enjoy now!

---

