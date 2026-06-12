---
title: "Wireless lan problem- is it getting worst? :/"
date: 2009-08-10
forum: Hardware
---

### Post by Moichim on 2009-08-10
Hey everybody.
I am new to Ubuntu (9.04) and linux and I am going in circles about how to set up my wireless PC card (trendnet tew-420pc) on my laptop (Thinkpad r51e).It was supposed to work out of the box according to wiki. I did get a few networks to show up on the top of the screen but it tried and tried to connect to no avail. (I am trying to get to a non secure, free, internet hotspot) 
I followed up very well all the fllowing thread to no avail too, and worst now: I dont even see networks at all ( [https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3AB1_(ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3AB1_%28ndiswrapper")) ) 
Lets see what I could post as an info on my system ?!:

betzaleldaniel@bina:~$ sudo iwconfig
[sudo] password for betzaleldaniel: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.


 betzaleldaniel@bina:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751F Fast Ethernet PCI Express (rev 21)
04:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)


betzaleldaniel@bina:~$ sudo ifup <ath0>
bash: syntax error near unexpected token `newline'


PLEASE HEEEEEELP

---

### Post by Moichim on 2009-08-10
solved... :) 
do I have to remove this thread? I dont think I could... :/

---

