---
title: "Wireless connects, but no data?"
date: 2011-06-07
forum: Hardware
---

### Post by ander111 on 2011-06-07
Hi guys,

I've installed Ubuntu 11.04 on my Toshiba NB255 netbook. I'm happy to find that audio now works, and I can control the screen brightness (two problems that kept me from using Ubuntu 10).

But now my wireless adapter doesn't work. Well, it *sort of* works... The router accepts our security key, and Ubuntu says I'm connected—but I can't get anything to load in Firefox.

Wireless has worked fine with Windows 7 (which is maddeningly slow, though, which is why I'd like to replace it with Linux, see) and with Linux Mint 9 (which unfortunately didn't handle power well, and cut my battery time in half).

I've searched and found many posts from people who couldn't connect—but once they connected, they had no problems. So this seems a bit different.

Where should I start? I'll be glad to post any info here you wish. Thanks for your help.

---

### Post by ander111 on 2011-06-07
Well, 48 views and no suggestions... I'm glad you're reading my post, though.  :?)

I saw another thread from someone with wireless problems, and they posted the output of these commands—so in case it helps:

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:47:d0:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3200 (3.2 KB)  TX bytes:3200 (3.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:4d:f0:da:aa  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::226:4dff:fef0:daaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7234 (7.2 KB)
```**iwconfig**

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"peachnet"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 2A:8D:1E:D7:08:71   
          Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```Finally—and I don't know if this has anything to do with the connection problem, but it is odd: I can't run Firefox by clicking (or double-clicking) its icon in the launcher. The icon "throbs" but nothing happens. When I run it from a command line ("firefox"), it *does* run, but then this message appears in the command window:
```
(firefox-bin:3550): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
```Thanks again, A.

---

### Post by ander111 on 2011-06-07
Well, I just tried [Linux Mint 11]("http://%22http://blog.linuxmint.com/?p=1760") and everything works fine, including wireless. Funny, it's based on Ubuntu&#8212;I guess LM's developers have done some extra tweaking. 

So, thanks anyway.  :?|

---

