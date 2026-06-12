---
title: "atheros AR2413/AR2414 Wfi  runs at 1 mbit"
date: 2012-09-04
forum: Hardware
---

### Post by stantonworrier on 2012-09-04
Hi All
I am new to lubuntu and have to say straight off that I am a fan :p.  I am looking for a point in the right direction to help me resolve an issue with an Atheros 802.11g cardbus nic.  the nic connects to the AP with no issues (using WPA personal) however the connection speed is painfully slow.
cherrygoround@cherrygoround:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"bs4wap"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C4:3D:C7:42:29:78   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:  0  Rx invalid crypt:  0  Rx invalid frag:  0
          Tx excessive retries:  0  Invalid misc:  0   Missed beacon:  0

eth0      no wireless extensions.

Can anyone point me in the right direction to resolve this please?

TIA
S

---

### Post by kurt18947 on 2012-09-04
Does your wifi *feel* like it's running at 1 mbit/sec?  I've had installs that said the same thing.  They were much faster than 1 mbit./sec.  Have you run a speed test?  Here are a couple choices:

[http://speedtest.net](http://speedtest.net)

[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

These will only check your internet connection speed but if your internet connection shows > 1mbit/sec. your network is obviously running faster.  I'm sure there are other utilities but I've never had a need for them.

---

### Post by stantonworrier on 2012-09-04
hi thanks for the response.  My Internet connection is a 60mbit cable connection. All the other warless devices run fine.  the laptop with the issue is very slow.  I think ther must be a configuration setting somewhere that needs editing.

S

---

