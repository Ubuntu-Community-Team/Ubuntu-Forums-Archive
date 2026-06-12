---
title: "keep wireless connected when Lenovo T61 goes to sleep"
date: 2010-01-14
forum: Hardware
---

### Post by Renton on 2010-01-14
I've got a Lenovo T61 that works great with Ubuntu 9.10. I've got a slight problem with the wireless card disconnecting or shutting down a few minutes after I shut the screen. Is there a setting that controls how long to wait before shutting down the wireless card?

a little info:

```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"RBG"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1E:58:FC:70:6B   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

```
~$ lspci | grep Atheros
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
```

I want to keep the wireless up so that I can continue streaming when the computer is shut. Does anyone have any ideas?

Thanks!

---

