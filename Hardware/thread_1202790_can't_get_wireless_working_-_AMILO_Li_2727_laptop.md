---
title: "can't get wireless working - AMILO Li 2727 laptop"
date: 2009-07-02
forum: Hardware
---

### Post by Dragonfi on 2009-07-02
I've just bought a **Fujitusu-Siemens AMILO Li 2727 laptop**, and installed Ubuntu 9.04 x64 on it.

Everything went fine, but I cannot get the wireless card working.

The wireless card in the machine is an **Atheros AR242x 802.11abg Wireless PCI Express Adapter**.

There is basically two ways I tried it so far:
1. I use the default **ath5k** drivere, wlan0 shows up, and I can set it up properly, but I cannot turn the card itself on (Led not blinking, cannot find the wireless network, and ifconfig wlan0 outputs the following flags: UP BROADCAST MULTICAST (but not RUNNING), etc.).

2. I use the **madwifi** (restricted) driver, and wlan0 not even show up.

I figured that it maybe just the key-combination that's not working, so I have tried downloading the **acerhk-source** package, and compiling a module(using module-assistant), and modprobing it, to activate the wireless key ( Fn+F1 ), but it still does not work. (getting the idea from this post: [http://ubuntuforums.org/showthread.php?t=986288](http://ubuntuforums.org/showthread.php?t=986288))

I don't really know what information or output would you need for further research, since there were no errors, it's just simply not working.

P.S.: Sorry if this post is not so clear, but I'm a bit tired since I've been doing this for the last 6 hour. :)

---

### Post by Dragonfi on 2009-07-15
Now some clarification, because my first post does not have all the information:
output of **iwconfig wlan0**:
```

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
output of **ifconfig wlan0**:
```

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:03:d2:2d  
          inet6 addr: fe80::222:5fff:fe03:d22d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:22129 (22.1 KB)

```

LED looks dead

Also I can set the parameters of wlan0, like the essid, encryption, etc.

---

