---
title: "Get restricted drivers without network"
date: 2011-06-15
forum: Hardware
---

### Post by lillem4n on 2011-06-15
So, my wired network card is broken but my wireless is working well. The problem is, it needs restricted drivers. And I need internet to install the restricted drivers. >_<

I'm probably a n00b-googler, but I really didnt find a way to manually install restricted drivers in Ubuntu.

I can get files to my laptop with my USB-memory, so all I need is to download the required files (but wich ones?) and either point the restricted driver install-thingy to them (how?) or manually install them (again, how?).

Please help. :)

---

### Post by 67GTA on 2011-06-15
It depends on your wireless card. If you can post the output of ```
lspci
``` from a terminal for us, someone can help you find the right driver.

---

### Post by lillem4n on 2011-06-16
I was just looking for a poke in the right direction, but a specific guide to my specific network card works great. ;)

Here is the output:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PC
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I guess its the "Broadcom B43 wireless driver" I want. But I dont know where to download it, wich files to get, where to put them or where to do the manual fixing. The "Hardware Drivers" tool is doing everything, very good, when you have an internet connection. :)

---

### Post by 67GTA on 2011-06-16
Check this page for a walk through. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access ]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access")
The b43 driver is included on the install CD, so it doesn't have to be downloaded. The firmware can be downloaded elsewhere, and then installed per the instructions. This should get you going.

---

### Post by MacHackers on 2011-06-16
> **lillem4n said:**
> So, my wired network card is broken but my wireless is working well. The problem is, it needs restricted drivers. And I need internet to install the restricted drivers. >_<

I'm probably a n00b-googler, but I really didnt find a way to manually install restricted drivers in Ubuntu.

I can get files to my laptop with my USB-memory, so all I need is to download the required files (but wich ones?) and either point the restricted driver install-thingy to them (how?) or manually install them (again, how?).

Please help. :)
Don't think it's possible (without an Internet connection). Do you have an ethernet port?

---

### Post by MacHackers on 2011-06-16
> **MacHackers said:**
> Don't think it's possible (without an Internet connection). Do you have an ethernet port?
Okay... Now that I have read your post throughly, go to Administration, Software Sources. Type in your password. Click around in that window and you can see that it says "Restricted Drivers". Click it. Now, with the Internet problem, you can buy a router from Walmart, Apple, or Cisco or something like that and plug in your ethernet cord to make it wireless.....  Or, you can go to a public place with Wireless Internet and see if that works! 

Thanks!

---

### Post by MacHackers on 2011-06-16
> **lillem4n said:**
> I was just looking for a poke in the right direction, but a specific guide to my specific network card works great. ;)

Here is the output:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PC
09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I guess its the "Broadcom B43 wireless driver" I want. But I dont know where to download it, wich files to get, where to put them or where to do the manual fixing. The "Hardware Drivers" tool is doing everything, very good, when you have an internet connection. :)
Oh.... I can help with that. Actually had to install this today... So, your in luck. Navigate to Administration, Hardware Drivers. It will search for the drivers you need. Now, when it pulls up "B43", click activate and It should work. That's what I did!

---

### Post by lillem4n on 2011-06-16
> **67GTA said:**
> Check this page for a walk through. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access ]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access")
The b43 driver is included on the install CD, so it doesn't have to be downloaded. The firmware can be downloaded elsewhere, and then installed per the instructions. This should get you going.

Perfect! Exactly what I needed! Thanks a lot. :) (writing this on my laptop. :D)

Machackers: My ethernet card is broken, and I do have internet access and WLAN in my apartement... And it was very much possible to install without internet, but via the guide above. :)

---

