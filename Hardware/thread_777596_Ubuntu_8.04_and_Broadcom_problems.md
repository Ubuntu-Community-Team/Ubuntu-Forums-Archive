---
title: "Ubuntu 8.04 and Broadcom problems"
date: 2008-05-01
forum: Hardware
---

### Post by zyryx on 2008-05-01
just upgraded to 8.04 and now I'm having problems with my wifi.
I switched to Ubuntu to resurrect a HP pavillion ze4500 that XP sp2 bricked (incompatible graphic drivers). with Ubuntu 7.10 I got the wifi to work fine. after the upgrade it didn't work of course, tried the solutions I found on the web, now my wifi can receive signals but not send. I can see network names, strength, and secure or not, but can not log on.

I am very new to Ubuntu and I'm struggling to learn command line, so simple and or detailed help would be great.

---

### Post by Ayuthia on 2008-05-01
Can you post your lspci -nn info?  Hardy is using kernel 2.6.24 which introduces some new wireless drivers that might be causing your problem.

---

### Post by zyryx on 2008-05-01
00:00.0 Host bridge [0600]: ATI Technologies Inc AGP Bridge [IGP 320M] [1002:cab0] (rev 13)
00:01.0 PCI bridge [0604]: ATI Technologies Inc PCI Bridge [IGP 320M] [1002:700f] (rev 01)
00:02.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:06.0 Multimedia audio controller [0401]: ALi Corporation M5451 PCI AC-Link Controller Audio Device [10b9:5451] (rev 02)
00:07.0 ISA bridge [0601]: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] [10b9:1533]
00:08.0 Modem [0703]: ALi Corporation M5457 AC'97 Modem Controller [10b9:5457]
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
00:0a.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
00:0c.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
00:10.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c4)
00:11.0 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility U1 [1002:4336]

---

### Post by Ayuthia on 2008-05-01
> **zyryx said:**
> 
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
This is your wireless card.  I am thinking that this should work with the b43 driver.  If you have a wired internet connection, you should try to install b43-fwcutter.  The process will ask you if you want it to find the driver for you.  If you say yes, it will load and install the driver for you.  After that, you should be ready to go.

I have not tried out installing b43-fwcutter from Synaptic in Hardy.  Another option is to find the Hardware Restricted Drivers from the menu.  I am using KDE so I am not for sure about where it is located.  If you get that up, it should give you the option to install the driver from there.

---

### Post by zyryx on 2008-05-01
followed the instruction on this site
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
no joy
tried to use the Synaptic installer
no joy

when I check Hardware Restricted Drivers, it says I have none

the wifi can still see the networks, signal strength, etc. it just wont send anything out...

---

### Post by omnibot on 2008-05-01
I was having the same problem. 

this thread fixed it for me, hopefully for you to :)

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

### Post by zyryx on 2008-05-01
I tried that page, I'd get to the "hardy bug fix" and it would all fall apart...

---

