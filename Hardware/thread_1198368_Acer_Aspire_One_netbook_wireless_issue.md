---
title: "Acer Aspire One netbook wireless issue"
date: 2009-06-27
forum: Hardware
---

### Post by iceman2 on 2009-06-27
I have a Acer Aspire One netbook ([http://www.amazon.com/Acer-AOA150-1447-8-9-Inch-Processor-Sapphire/dp/B001EYV9TM](http://www.amazon.com/Acer-AOA150-1447-8-9-Inch-Processor-Sapphire/dp/B001EYV9TM) )and installed Ubuntu 8.04..
I followed the docs in [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) to install the madwifi drivers ,but its not working after following the steps...there's two entries when i do iwconfig or ifconfig  ...ath0 and wifi0

---

### Post by Hobgoblin on 2009-06-27
Why 8.04?  Wifi support is much improved in both 8.10 and 9.04

---

### Post by iceman2 on 2009-06-28
I just had 8.04 .. no specific reason

---

### Post by iceman2 on 2009-06-28
The NetworkManager doesn't detect/show any wireless Access Points.

```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

$ iwlist ath0 scan
ath0      No scan results


$ iwlist wifi0 scan
wifi0     Interface doesn't support scanning.
```

---

