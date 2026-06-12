---
title: "wireless fun with SL500"
date: 2009-03-27
forum: Hardware
---

### Post by supremedalek on 2009-03-27
I installed ubuntu 8.10 in my recently bought SL500 and still am having issues with its wireless card. From what I've gathered it is a Atheros AR5BHB63. According to [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default]("http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default"), it I made sure the ath5k drivers were installed. And it works fine most of the time. But, like today, I used it at home fine, then went to campus and used its wireless. It too worked fine. But when I got home, it is not working; I am using its wired port right now. So, I asked the machine what it knew about its own wireless card:

```

raub@monaco:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:smileysurprised:ff   Fragment thr=2352 B   
          Power Management:smileysurprised:ff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

raub@monaco:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:23:4e:d8:39:4b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

raub@monaco:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

raub@monaco:~$ 
```

It sounds like the machine knows the card is there but it is just not seeing the wireless network. I have been able to get the wireless running by reinstalling the ath5k drivers once again. Why is that happening?

---

