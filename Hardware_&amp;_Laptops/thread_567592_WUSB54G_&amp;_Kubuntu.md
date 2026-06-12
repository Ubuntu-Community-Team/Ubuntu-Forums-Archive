---
title: "WUSB54G &amp; Kubuntu"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by kylecroft on 2007-10-04
Hi

I recently installed Kubuntu 7.04, and I need help hooking up my WUSB54Gv4. Here are some outputs:

lsusb:
```
Bus 001 Device 002: ID 13b1:000d Linksys
```

iwconfig
```
rausb0    RT2500USB WLAN ESSID: "linksys"    Nickname:""
                         Mode: Mangaed Frquency=2.435 GHz Access Point: 00:13:10:E2:97:07
                         Bit Rate=54 Mb/s
                         RTS thr:off       Fragment thr: off
                         Link Quality:72/100  Signal level: -77 dBm  Noise level: -85 dBm
                         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                        Tx excessive retries:0  Invalid misc:0  Missed beacon:0
```

iwconfig rausb0 commit
```
Error for wireless request "Commit changes" (8B00) :
           SET failed on device rausb0 ; Operation not permitted.
```

Any help would be greatly appreciated.

Thanks

Kyle

---

