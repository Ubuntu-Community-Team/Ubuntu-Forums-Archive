---
title: "Slow Wifi connection with Ubuntu"
date: 2012-02-02
forum: Hardware
---

### Post by pternet on 2012-02-02
Hi!
I'm a Linux newbie and I've just installed Ubuntu 11.04 with Wubi alongside Windows Xp. The problem is the connection speed varies between 5-11 Mb/s, according to the speedtest.net the download speed is 0.37 Mbps, the upload is 3.66 Mbps. On the same pc i get over 18 Mbps download speed, the upload speed is around 6-7 Mbps. Also tried with Ubuntu 11.10 same results. 
Plz help, thank you

---

### Post by pternet on 2012-02-02
*The 18 Mbps refers to when i'm running Windows XP

---

### Post by kurt18947 on 2012-02-02
Deleted.  Formatting issues.

---

### Post by pternet on 2012-02-02
It's a PCI wifi card, lspci gives me this:

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 71c3 (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Device 71e3 (rev 9e)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:05.0 Network controller: Ralink corp. RT2500 802.11g (rev 01)

---

### Post by kurt18947 on 2012-02-02
I'm even less well versed with Ralink than I am with other chipsets.  Some of the newer Ralink chipsets are the subject of much discussion but RT2500 isn't usually one of them. I hope someone will be along with some thoughts.  Sorry I can't be of more help.    

Edit:  Here's a thread with a similar problem if you haven't seen it.  Perhaps there's something with 11.04.  [http://ubuntuforums.org/showthread.php?t=1742267&highlight=RT2500](http://ubuntuforums.org/showthread.php?t=1742267&highlight=RT2500)  

Edit 2: You have good internet speed in XP. You might try downloading 11.10 and create a live CD or live USB. Boot from that and see if your speed problem persists.

---

### Post by pternet on 2012-02-02
I've done some research, and I have installed Wicd to replace the native network manager, and it's better, the network info now shows 54 MB/s and now the speed has gone up to about 1.1 Mbps, which needless to say, is still terribly slow. Any other ideas?

---

