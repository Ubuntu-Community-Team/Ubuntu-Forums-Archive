---
title: "linux cant turn on wireless card"
date: 2009-04-16
forum: Hardware
---

### Post by Hellbike on 2009-04-16
Linux cant turn on my wireless card (device?), broadcom 802.11b/g WLAN. 
After restarting laptop and choosing windows - he also cant turn if on. I have to turn off and turn on laptop, and then windows turns it on.

```
hellbike@hellbike-laptop:~$ sudo ifconfig
[sudo] password for hellbike: 
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:63:c5:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)
```

```
hellbike@hellbike-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

```
hellbike@hellbike-laptop:~$ sudo iwlist wlan0 scanning
wlan0     Interface doesn't support scanning : Network is down

```

```
hellbike@hellbike-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


```

```
ifconfig wlan0 up

SIOCSIFFLAGS: No such file or directory


```

---

### Post by springbokmarine on 2009-07-14
I have the exact same problem in Debian Lenny. I installed and got everything working. The wifi card is a PCMCIA card (BCM4318). Once I rebooted, it seems that the card turned off and even thought info shows up in iwconfig as wlan0, the lights on the card doesn't come on anymore, nor is it seen under ifconfig.

The only other post I could find: 

[http://ubuntuforums.org/archive/index.php/t-603941.html](http://ubuntuforums.org/archive/index.php/t-603941.html)

---

