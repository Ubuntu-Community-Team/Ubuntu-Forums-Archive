---
title: "Problems with Dynex PCI wireless device"
date: 2008-10-22
forum: Hardware
---

### Post by Daimoneze on 2008-10-22
This is a fresh install of Hardy. It is not possible to plug a CAT5 into this machine. The driver shows in Restricted Drivers but I get an error message involving firmware. Here are the outputs to lspci and iwconfig.

```
01:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Daimoneze on 2008-10-22
I just realized there is a networking and wireless forum. My mistake. I suppose an admin will move it if it's a problem. Sorry!

---

