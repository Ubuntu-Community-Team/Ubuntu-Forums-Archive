---
title: "Problems connecting to WEP network."
date: 2006-03-24
forum: Hardware &amp; Laptops
---

### Post by Liberty is Me on 2006-03-24
I need to know how to connect to a wireless network from the terminal using WEP.  I've played around with iwconfig, but I don't think my syntax is correct. Here is what I've done so far.

First I did:
```
ifconfig eth1
```
which gave me
```
eth1      Link encap:Ethernet  HWaddr 00:04:E2:87:D9:11
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

```
Followed by:
```
iwconfig eth1
```
and this gave me the following:
```
eth1      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Access Point: 00:00:00:00:00:00   Bit Rate:11 Mb/s
          Tx-Power:off
          Retry limit:3   RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Next I ran:
```

iwlist eth1 scan
eth1      No scan results

```

and then 
```

sudo ifconfig eth1 up
```
and then
```
iwlist eth1 scan
```

which gave the following: 
```
eth1      Scan completed :
          Cell 01 - Address: 00:80:C8:1D:77:9B
                    ESSID:"The Pizza Box"
                    Mode:Master
                    Channel:6
                    Quality:0  Signal level:0  Noise level:0
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
```
and concluded with the following:
```
iwconfig eth1
eth1      IEEE 802.11b  ESSID:"The Pizza Box"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:80:C8:1D:77:9B
          Bit Rate:11 Mb/s   Tx-Power:42 dBm
          Retry limit:3   RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0
```

I've played around with various ways of iwconfig a couple nights ago and couldn't get it to work.  "The Pizza Box" is the name of the network i want to connect to and I have the WEP key.  In searching for the ansewer to this question on the forum I found that it mattered if the key was numbers or alpha-numberic.  The key is alpha-numberic.  Can anyone help me or point me in te right direction?  Thank you in advance for any help you would be willing to provide.

---

