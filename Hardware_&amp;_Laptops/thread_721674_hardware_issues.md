---
title: "hardware issues"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by linux1time on 2008-03-11
im desperate...i have no sound...i have no wifi...i am tryng to run linux ubuntu 7.10..on a laptop acer 5315...today ive mentioned my boss that linux is alright and would made an excelent substitute for windows and what will i say to him tommorow when i arrive there whith my work laptop all ruined ????can somedy help me please?i kind of desperate...

---

### Post by solar george on 2008-03-11
Open a terminal and type,

```
lspci
```

Post the output.

---

### Post by linux1time on 2008-03-11
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

here itt is...

---

### Post by solar george on 2008-03-11
> ```
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

Well that's your wifi card.

Try [http://ubuntuforums.org/showthread.php?t=718075](http://ubuntuforums.org/showthread.php?t=718075)

---

### Post by linux1time on 2008-03-11
did not understand very well...can somedody explain more simply about putting my wifi and sound to work please?

---

### Post by oldsoundguy on 2008-03-11
for the wi fi: (since it is an Atheros chip, it should have installed.)
go to: 
System> Administration> Network>
sign in
highlight wireless connection then select properties
(for a fixed location uncheck roaming mode .. for travel have it checked)
find the network you need in the first box
select it and fill in the information required by your specific networl (Your IT should have that info)
save and exit and you should be on line 

if not control/alt/backspace and sign in again and that should do it.

Sorry on the sound. No experience with the Intel sound chip. (audio controller)

---

### Post by linux1time on 2008-03-11
done what...wirelles doesnt appear....only network something about roaming and modem conexion,no wifi or wireless and ive seen thatthe restricted driver is enabled

---

### Post by oldsoundguy on 2008-03-11
The driver for Atheros  should have installed when you installed the system, but it IS a laptop, so all bets are off.  (proprietary stuff .. sometimes takes more to get them running).  I am NOT a laptop user, but thought I could help with the network .. sorry it does not hook up.

---

### Post by mnallen on 2008-03-11
I'm unfortunately not going to be extremely helpful, but I can say I'm having the exact same problem.  I'm a second time Ubuntu user.  I used a distro last summer on a laptop and had it working fine.  That computer died since then, and I now have a laptop that came with Vista.  I downloaded Ubuntu Ultimate 1.7 because I'm lazy and have been working ever since to get the wireless working.

The computer starts into Ubuntu with the wifi turned off.  But after turning it on, it still doesn't show up in the networking list.  Just wired and modem connection.  

Another point worth making is that my restricted drivers list shows that I also have an Atheros card.  It says that it's installed and in use, but it doesn't seem to be doing much.  

I'm wondering if there's just a compatibility problem.  I was reading in a help file that it's possible to use the windows driver somehow.  But I'd hate to start messing with that if it's the wrong way to go.  

I'm not saying I'm a master with Linux, but I've used it enough to know this is more than just a new user misunderstanding.  Just don't know quite what it could be.

Thanks for any suggestions!

---

### Post by mnallen on 2008-03-11
Just to clarify, I'm sorry if my last post was misleading.  I'm having the exact same wireless problem.  My sound is fine. The two problems are probably quite unrelated, so I wasn't thinking about sound.  Good luck with sound, but I don't know what to say about it.

---

### Post by solar george on 2008-03-12
Try following this howto:

[https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html)

---

### Post by morrison1977 on 2008-03-13
I have the same problem, lspci lists: 05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
but it doesn't show up in network manager, I've tried downloading the latest madwifi drivers and installing them, didn't work, and tried with windows wireless drivers.  I still don't see wireless networks.  I would greatly appreciate any help.  Thanks.

---

