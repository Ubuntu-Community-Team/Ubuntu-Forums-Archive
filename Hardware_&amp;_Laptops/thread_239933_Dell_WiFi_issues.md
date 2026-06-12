---
title: "Dell WiFi issues"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by Anti Hero on 2006-08-20
I have a Dell Inspiron E1505 with a Dell Wireless 1390 WLAN Mini-Card. I would like to know how to configure Ubuntu so I can use my WiFi on my house/school networks. I am currently using the LiveCD feature rather than a full install just to see how I like it. If it is impossible to do this that is ok, I'd just like to know if I could do this. Thank you for your help and I'm sorry if this has been posted before, but I did a quick search and didn't find any answers. Thank you again.

- Anti Hero

---

### Post by H.E. Pennypacker on 2006-08-20
I am pretty sure the card's chipset (identification name/number) is from Broadcom, a company that makes many wirelss cards.  It's notoriously known for giving Linux users a hard time, but like many other Broadcom users, I've gotten it to work.

To see if you do have a Broadcom card, check out Device Manager.  System > Device Manager.  Under PCI Bridge, see if there's something called "Broadcom".  If it is, take that name (in my case, it is "BCM4318"), and do a forum search.

Yours will likely be "BCM"-something.  It may even be the same as me (BCM4318).

---

### Post by Anti Hero on 2006-08-20
Ok, under Network Adapters (I did not have a section called PCI bridge)it says I have a 1934 Net Adapter, a Dell Wireless 1390 WLAN Mini-Card, and a Broadcom 440x 10/100 intergrated controller. Am I looking in the right place? If so, do I just do a search for the Broadcom 440x 10/100 on forums?

---

### Post by Anti Hero on 2006-08-21
I don't know how this forum feels about bumping topics, but I would really like some help with this please.

---

### Post by smelly_sox on 2006-08-21
My DELL C640 has the Intel PRO/Wireless 2200BG & it worked straight up
I can try to help you, but I'm no expert.

/Applications / Accessories/ Terminal
*lspci|grep Network*
Please post results
Or even just *lspci* and look for all of the entries regarding network hardware & post.
Then we can google the results for more info

Regards

---

### Post by Anti Hero on 2006-08-21
These are the results from lspci
```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
ubuntu@ubuntu:~$


```
So does this mean that I just have to search for the Intel 82801G?

---

### Post by smelly_sox on 2006-08-21
Basically every device listed in this file should be working for you. Relevant lines for network devices:
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
This will be your LAN port.

0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
This will be your wireless card.
Unknown device means your kernel does not have support for this device. There is no mention of any Dell Wireless 1390 WLAN Mini-Card. A quick google and the Dell Wireless card seems to be based upon Broadcom's 43xx chipset. So please read [this thread from ubuntu forums.]("http://www.ubuntuforums.org/showthread.php?p=1386521")

Regards

---

### Post by Anti Hero on 2006-08-22
Thanks for the help, I really appreciate it. I'll post again if everything is working ok, or not :D

---

### Post by Cryonic on 2006-08-22
My Dell has the same wireless mini-card, I got it working with the instructions in this thread:

[http://www.ubuntuforums.org/showthread.php?t=193350](http://www.ubuntuforums.org/showthread.php?t=193350)

---

