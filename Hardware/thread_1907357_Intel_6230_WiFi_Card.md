---
title: "Intel 6230 WiFi Card"
date: 2012-01-11
forum: Hardware
---

### Post by ThePol1 on 2012-01-11
I have a Dell Mini 9 running Ubuntu 11.10. I bought a new Intel 6230 wireless card because I wanted to move from G to N (5 Ghz). It was correctly detected by Ubuntu out of the box.
 
The card supports the 5 Ghz range and my router does as well (Linksys E3000 running DD-WRT). I am using WPA2 as my security protocol.
 
For some reason, however, I can't connect via N. Any suggestions?
 
lspci -k shows:
```
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
        Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn
```
 
iwconfig shows:
```
wlan0     IEEE 802.11abgn  ESSID:"**********"
          Mode:Managed  Frequency:2.412 GHz  Access Point: ***********
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:142   Missed beacon:0
```
 
iwlist auth shows:
```
wlan0     Authentication capabilities :
                WPA
                WPA2
                CIPHER-TKIP
                CIPHER-CCMP
```

---

### Post by ThePol1 on 2012-01-11
I think it may make sense for me to move my post to the Wireless area. I'll look into doing that...

---

### Post by ThePol1 on 2012-01-12
This wasn't a problem with my new wireless card -- it is working just fine in 11.10.  A restart on my router and now I can see my N (5 Ghz) SSID!

---

