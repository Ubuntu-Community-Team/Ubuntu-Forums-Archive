---
title: "No hardware present for USB WIFI CNet CWD-854 using ndiswrapper"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by Sood on 2006-03-28
Hello, I followed the instruction from [http://doc.ubuntu-fr.org/materiel/wifi/ndiswrapper]("http://doc.ubuntu-fr.org/materiel/wifi/ndiswrapper").

I checked the compatibility of my key USB Wifi on [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#C]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#C") :

> Card: CNet CWD-854 Wireless-G USB Dongle

    * Chipset: RT2570
    * usbid: 148f:2570
    * Driver: Windows 2000 drivers from installation CD, cd version 1.09, file rt2500usb.inf
    * Other: using NdisWrapper-utils Ubuntu package 0.12+1.0rc2-1, Kernel 2.6.10
    * Other: Needed to " modprobe --remove ehci-hcd " to make it work.
    * Other: Windows 2000 drivers from v1.12 CD did not work (kernel Oops on shutdown).

I had downloaded the driver from CNET site [http://www.cnet.com.tw/download/cwd-854.htm]("http://www.cnet.com.tw/download/cwd-854.htm") and I had even used CD (driver win2000), and there is no "hardware present" but only "driver present" 

```

>sudo ndiswrapper -i /opt/Win2k/rt2500usb.inf
>sudo ndiswrapper -l
Installed ndis drivers:
rt2500usb driver present

```

I have a Linksys wireless router without any problem.

Thanks for you answer.

---

