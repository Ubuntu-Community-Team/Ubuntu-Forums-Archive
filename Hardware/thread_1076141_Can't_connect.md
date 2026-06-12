---
title: "Can't connect"
date: 2009-02-21
forum: Hardware
---

### Post by Zer017 on 2009-02-21
Hi!

I've installed Linux 8.04. I did a dualboot with Vista.
I can use both wire and wireless connection with Vista but nothing with Linux. Why?

I've a D-Link DWA-547. 

Also, I'm a newbie trying to learn Linux, just so you know ;)

---

### Post by jklm459 on 2009-02-21
Yoocart is a leading worldwide wholesaler company (or u can say organization). We supply more than 100 thousand high-quality merchandise and famous brand name products all at [Wholesale](http://www.yoocart.com) prices. Start your [Wholesale](http://www.yoocart.com) sourcing here today and experience first class service and fast shipping.If you want to learn more, so stay tuned [http://www.google.com/reader/shared/13118345408017647681?hl=zh_CN](http://www.google.com/reader/shared/13118345408017647681?hl=zh_CN), if you feel that our information useful to you, you can at any time through RSS Subscribe concern, we will sincerely serve you.

---

### Post by konqueror7 on 2009-02-21
stop spamming!

oh btw, try using a static configuration for your connection...copy the same details of your dhcp and make a static configuration with the details...see if that works...

---

### Post by sahabcse on 2009-02-21
Hi 

Check your network card and driver are detected. Using the command #lspci , You can easily find out the NIC card information.
eg)

=====================================================================
sahab@sahab:~$ sudo lspci
[sudo] password for sahab: 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
**01:05.0 [COLOR="Red"]Ethernet controlle[/COLOR]r**: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
==================================================================

For setting up the network follow the below url

============================================
[http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html](http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html)
============================================

Regards
Sahab

---

