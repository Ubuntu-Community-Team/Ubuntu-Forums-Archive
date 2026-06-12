---
title: "Wireless stopped working! Please help!"
date: 2008-10-15
forum: Hardware
---

### Post by ojve on 2008-10-15
Today my wireless interface suddenly stopped working in Intrepid. I'm guessing it was because of the upgrade this morning. I don't think it's too difficult to solve it, I just have no idea how! The interface is still detected by iwconfig, but not is not there either in ifconfig or the network-manager.

Please help me with this as I'm really depending on my wireless connection!

This is the output of ifconfig and iwconfig, the wireless interface used to be called eth1 I think:
```


thomas@LapTorkel:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:68:cd:67
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:29970 (29.9 KB)  TX bytes:29970 (29.9 KB)

thomas@LapTorkel:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=0 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

Thx a lot!
//T

---

### Post by ojve on 2008-10-15
Actually, nevermind. After another update, the wireless works fine again.

//T

---

