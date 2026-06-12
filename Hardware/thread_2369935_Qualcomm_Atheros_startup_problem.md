---
title: "Qualcomm Atheros startup problem"
date: 2017-08-28
forum: Hardware
---

### Post by mozart75 on 2017-08-28
Hi, I have a Dell Inspiron 3437 with dual boot UEFI using Ubuntu 17_04 using a ISO downloaded from internet. I installed realtime for sound recording during standard installer use.
My system startup is taking an eternity, apparently due to a problem in the wireless network device.

This is an excerpt of my output from dmesg:

[   17.441752] audit: type=1400 audit(1503946514.058:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=818 comm="apparmor_parser"
[B][COLOR=#ff0000][   17.720538] usb 1-1.6: device descriptor read/64, error -110[/COLOR]
[/B][   17.954685] r8169 0000:07:00.0 enp7s0: link down
[   17.954687] r8169 0000:07:00.0 enp7s0: link down
[   17.954738] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
[   19.575207] r8169 0000:07:00.0 enp7s0: link up
[   19.575216] IPv6: ADDRCONF(NETDEV_CHANGE): enp7s0: link becomes ready
[B][   23.125909] usb 1-1.6: New USB device found, idVendor=0cf3, idProduct=0036
[   23.125912] usb 1-1.6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[/B][   99.375970] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   99.375972] Bluetooth: BNEP filters: protocol multicast
[   99.375975] Bluetooth: BNEP socket layer initialized
[  103.319605] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[  103.331903] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[  103.351997] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[  104.379600] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[  105.469808] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[  105.522974] wlp6s0: authenticate with 74:31:70:8f:e1:91
[  105.534755] wlp6s0: send auth to 74:31:70:8f:e1:91 (try 1/3)
[  105.537932] wlp6s0: authenticated
[  105.538112] ath9k 0000:06:00.0 wlp6s0: disabling HT as WMM/QoS is not supported by the AP
[  105.538115] ath9k 0000:06:00.0 wlp6s0: disabling VHT as WMM/QoS is not supported by the AP
[  105.543120] wlp6s0: associate with 74:31:70:8f:e1:91 (try 1/3)
[  105.564486] wlp6s0: RX AssocResp from 74:31:70:8f:e1:91 (capab=0x431 status=0 aid=1)
[  105.564606] wlp6s0: associated
[  105.564620] IPv6: ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready
[  109.371884] ip6_tables: (C) 2000-2006 Netfilter Core Team
[  109.775476] Ebtables v2.0 registered

More information:
lspci -nnk | grep 0280 -A2
06:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter [1028:020c]
    Kernel driver in use: ath9k

Exactly at 23 secs after Ubuntu starts, the HD stops blinking for more than one minute. Nothing is shown on screen during that time.
I already run the EPROM selftest software with nothing wrong reported. 
This wireless always gave me a lot of headaches, in Windows there were several times it just refused to turn on. In Linux, ONCE it stopped working completely for about 5 minutes, then turned on and started working as if it was a good kid.
I don't mind if sometimes it does not work for a while, what really pisses me off is this slow start.

Any suggestions?

---

### Post by jeremy31 on 2017-08-29
I would try this to disable the bluetooth device on the Atheros card
```
sudo -H gedit /etc/udev/rules.d/81-bluetooth-hci.rules
```
Paste the following
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="0cf3", ATTRS{idProduct}=="0036", ATTR{authorized}="0"
```
Save file and reboot

---

