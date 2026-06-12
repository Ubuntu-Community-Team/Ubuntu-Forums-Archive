---
title: "wifi connectivity issues. my laptop, router, or ubuntu?"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by mjkelly on 2007-09-20
Heres whats going on. Im using a brand new gateway laptop with built in wifi. When i load into ubuntu, it sometimes finds my router, sometimes it doesnt. Im using a hawking HWR54G wireless and wired router. Its not the best router or anything, but i dont know if that explains whats wrong. Like i said sometimes it will find it and connect. It will work fine for like 1-15 minutes then D/C. Then it might find the net back up and reconnect or it might not find it at all. None of the apps i have installed find the net. It will say no wireless networks detected.

So in short, it sometimes finds the net and works for a lil bit then D/Cs and may or may not reconnect. I dont know if its my laptop, the router which is located literally 1 foot from the lap top, or Ubuntu. It also has the same connectivity problems upstairs and in the living room 20 feet away.

Is connectivity a problem with feisty?


Heres my iwconfig:
wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Heres my iwlist scanning:
:~$ sudo iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning : Operation not supported

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:52:F1:AC
                    ESSID:"hawking"
                    Mode:Master
                    Frequency:2.462 GHz
                    Quality=48/64  Signal level=65/65  
                    Encryption key:off
                    Extra:tsf=000000150d4d112c

So there it located the net but if i connect to it the previous problems are encountered.

Thanks in advance guys. Ive been coming to these forums for years now and i know the help here is unequalled. If you guys need any further information, ill be checking here regularly.

Thanks,
Marty

---

### Post by mjkelly on 2007-09-20
Noone? Should i cross post this in network forum?

---

