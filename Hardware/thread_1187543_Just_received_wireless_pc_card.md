---
title: "Just received wireless pc card"
date: 2009-06-14
forum: Hardware
---

### Post by iAndrew on 2009-06-14
```
drew@Professional:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0f:b5:a4:ac:0f  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fea4:ac0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:180227 (176.0 KB)  TX bytes:22209 (21.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:0d:60:38:46:af  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63100 (61.6 KB)  TX bytes:63100 (61.6 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-B5-A4-AC-0F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2529 errors:0 dropped:0 overruns:0 frame:171
          TX packets:286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:424827 (414.8 KB)  TX bytes:32369 (31.6 KB)
          Interrupt:11 

```

Basically I bought a netgear card, and I tried to disable the onboard wireless (to save power). Can anyone decipher this and tell me what it means?

Why I have more than 1 thing ~ and if possible could anyone please tell me what each one does?

---

### Post by nick125 on 2009-06-14
> **iAndrew said:**
> ```
drew@Professional:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0f:b5:a4:ac:0f  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fea4:ac0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:180227 (176.0 KB)  TX bytes:22209 (21.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:0d:60:38:46:af  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63100 (61.6 KB)  TX bytes:63100 (61.6 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-B5-A4-AC-0F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2529 errors:0 dropped:0 overruns:0 frame:171
          TX packets:286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:424827 (414.8 KB)  TX bytes:32369 (31.6 KB)
          Interrupt:11 

```Basically I bought a netgear card, and I tried to disable the onboard wireless (to save power). Can anyone decipher this and tell me what it means?

Why I have more than 1 thing ~ and if possible could anyone please tell me what each one does?

Try disabling your onboard wireless in the BIOS.

---

### Post by n4mgr on 2009-06-14
eth0 is your lan connection, i.e wired
ath0 is your onboard wireless
wifi0 is your outboard wireless, pcmcia I would guess
lo is as it says, local loopback

You should as the previous poster said disable the inboard wireless via the bios or check and see if there is a switch somewhere on the pc which controls that module. It may be that even with it switched off you will still need to disable it in the bios to truly take it offline.

---

### Post by iAndrew on 2009-06-14
> **n4mgr said:**
> eth0 is your lan connection, i.e wired
ath0 is your onboard wireless
wifi0 is your outboard wireless, pcmcia I would guess
lo is as it says, local loopback

You should as the previous poster said disable the inboard wireless via the bios or check and see if there is a switch somewhere on the pc which controls that module. It may be that even with it switched off you will still need to disable it in the bios to truly take it offline.

I just checked and the onboard/internal wireless is disabled.

---

### Post by n4mgr on 2009-06-14
> **iAndrew said:**
> I just checked and the onboard/internal wireless is disabled.

Is the outboard wireless card working for you? There are a few pretty decent apps available through synaptic that will basically help you control the card if you like I will give you a list. I installed them on mine, but don't remember right off hand what the names are. 

BTW - There is an app on Facebook called apps for Ubuntu that I highly recommend. It has quite a few and you can install directly from there.

---

