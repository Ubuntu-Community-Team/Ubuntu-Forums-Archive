---
title: "[wlan] linksys wifi card doesn't work"
date: 2005-06-04
forum: Hardware &amp; Laptops
---

### Post by Reeva on 2005-06-04
Hi, I installed ndiswrapper on ubuntu HH. Everything went ok up until and including 'modprobe ndiswrapper'. The installation instructions say that if the modprobe step went ok and if the correct files are in /etc/ndiswrapper, the card should be up and running. But that does not seem to be the case. The card is not receiving any power. 
running ifconfig gives :
```
wlan0     Link encap:Ethernet  HWaddr 00:12:17:DF:EE:DC
          inet6 addr: fe80::212:17ff:fedf:eedc/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2430 (2.3 KiB)
          Interrupt:16

``` 

running iwconfig gives:

```
wlan0     IEEE 802.11g/b+  ESSID:"reeva"  Nickname:"lexje"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

If I scan " iwlist wlan0 scanning " it say's " no scan result "

what can I do ? ;(
BTW, the card is a Linksys WPC54G 

ps : lspci get's this :
```
0000:03:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```

Thank you!

---

### Post by Reeva on 2005-06-05
someone ? :$

---

### Post by spd106 on 2005-06-05
Hi, have you looked through this for some ideas?
[http://ubuntuforums.org/showthread.php?t=5645](http://ubuntuforums.org/showthread.php?t=5645)

Ok it is for warty, but it may lead to some success.

Check the revision number of the card.
If you can't find any APs then the card isn't working right(assuming you are within range), maybe try a different driver.

---

### Post by kleeman on 2005-06-05
Try:

sudo dhclient wlan0

and

sudo iwconfig wlan0 scanning

---

