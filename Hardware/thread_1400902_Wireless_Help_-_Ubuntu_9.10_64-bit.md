---
title: "Wireless Help - Ubuntu 9.10 64-bit"
date: 2010-02-07
forum: Hardware
---

### Post by izizzle on 2010-02-07
I'm running Ubuntu 9.10 64 bit on an HP Dv9005us. The internal wireless went out a while ago. I just installed Ubuntu today and am running into issues with my wireless. I'm using a USB TendNet TEW-424UB adapter and the internet connects- but there is a catch.

1. It is horribly slow- tried to update and was getting around 1-5 kbps.
2. The adapter only seems to work on 1 USB port, Ubuntu reads it on the other ports but it does not connect. 
3. It is a wireless G adapter, but it is oly running in wireless B mode.

Here is my iwconfig: ```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan5     IEEE 802.11bg  ESSID:"ZRES"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:47:3D:B9   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by izizzle on 2010-02-07
I also tried with an Airlink AWLL3028 Wireless USB adapter, and ubuntu recognizes it, but same issue- it does not connect with the network!

---

### Post by izizzle on 2010-02-07
Tried the airlink with WICD, and still no luck. It doesn't get past "Obtaining IP Address..."

Any help is greatly appreciated guys....

---

### Post by izizzle on 2010-02-07
I'm currently downloading the 32 bit version of Ubuntu 9.10. Do you guys think this would help with the wireless issues?

---

### Post by pi/roman on 2010-02-07
See this thread:
[http://ubuntuforums.org/showthread.php?t=677212&page=2](http://ubuntuforums.org/showthread.php?t=677212&page=2)
It looks like the Airlink requires ndiswrappr to work. Maybe the trendnet would need ndiswrapper too.

---

### Post by izizzle on 2010-02-08
The weird thing is: The guy I bought the laptop from (I bought it a few days ago) had the trendnet adapter plugged into Ubuntu 9.04 and it was working fine, just plug and play. I don't know if he was running 32 or 64 bit, but it was indeed Ubuntu. Shouldn't it work on 9.10 as well?

---

