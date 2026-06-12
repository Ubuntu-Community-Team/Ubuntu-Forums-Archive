---
title: "Neither wired nor wireless network connection"
date: 2010-05-15
forum: Hardware
---

### Post by aleeds on 2010-05-15
I just installed Xubuntu 10.04 on my acer emachines netbook and I can't connect to the internet neither using a wire or wireless network now. Regarding the wired network it don't think it even recognises that there exists hardware. If I run ```
lspci
``` it lists my wireless card which is broadcom BCM4312 802.11b/g but it doesn't mention any ethernet. 
Running ```
ifconfig 
``` returns: 
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5360 (5.3 KB)  TX bytes:5360 (5.3 KB)

```So it doesn't have any eth0 or eth1 as expected. I don't know what that lo thing means. 
After searching some solutions to the problem it turns out I need firmware for my wireless card. To install this I should however run 
```
sudo apt-get install b43-fwcutter
```which I cannot do since I don't have an internet connection. Can I somehow just download the package so that I can move it on a usb stick and install it not using apt-get install? 
Regarding the problem with the wired connection however I have not found anything.

---

