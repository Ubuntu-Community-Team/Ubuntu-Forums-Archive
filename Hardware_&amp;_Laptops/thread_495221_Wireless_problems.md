---
title: "Wireless problems"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by RealEmotionX on 2007-07-07
Okay, I am helping a freind install linux on her laptop.

everything is going fine except I cant get her wireless working, at all

she has a Acer Aspire 3100

I think it may be a driver problem and I have tried the programs WiFi Radar and KWiFimanager

---

### Post by ceargle on 2007-07-07
Could you post the output of ```
lspci
``` so we know what type of wireless card is being used?

---

### Post by RealEmotionX on 2007-07-07
I thought about it, I was just being lazy

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

---

### Post by RealEmotionX on 2007-07-08
any ideas? She does want her laptop back and if I cant give it wireless functionality I will put XP on it instead

---

### Post by ceargle on 2007-07-08
Found this thread: [http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")

The wireless card in her laptop is the same found in that guide.  It should be fairly straightfoward.  Unfortunately that chipset is a bit harder to get working than other cards, post any questions you might have from the guide :)

---

### Post by jimbob on 2007-07-08
The above post worked for me straight away also giving 54Mbs.

If you use the Ubuntu bcm43XX driver the best you will get is 11Mbs.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by RealEmotionX on 2007-07-20
sarah@kyle-laptop:~$ sudo ndiswrapper -l
bcmwl5 : invalid driver!
WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 's#'
bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
bcmwl5.sys : invalid driver!

---

### Post by -::Bas::- on 2007-07-24
Ok, sorry to kick this topic, but does this mean you've got the wireless working?

I am thinking of buying a laptop for my daily train-journeys and the best offer I've found is one with this wifi chip in it, and since that will be quite essential, I would like to know whether it's possible to get this chip to work with Ubuntu..

---

