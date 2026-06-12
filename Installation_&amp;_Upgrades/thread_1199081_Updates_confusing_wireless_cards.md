---
title: "Updates confusing wireless cards"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by dArAzAc on 2009-06-28
Hello,

I've a vanilla install of Ubuntu Jaunty which I reinstalled because (with my original install) Ubuntu stopped recognizing my wireless card *only after *performing a package update. Normally I would just check install every update, but never again. I tried various ways to get the card back up until I eventually gave up (I have a troublesom Broadcom card).

Well now I am obviously hesitant to update my system, but I still want to be up-to-date. Which updates could cause a potential interference with the detection of my wireless card?

---

### Post by starcraft.man on 2009-06-28
Do you know exactly which packages you installed that broke your wireless support? As you noted, I really don't recommend not updating from any given point, this means you won't receive security fixes or updates in functionality. 

I'm gonna go out on a limb though and guess that the only two packages that could have caused this trouble would be network-manager and/or wpasupplicant, and it's probably the latter. One possible solution (though not ideal by any means) is to do a vanilla install and then lock the version of wpasupplicant so that it never updates. The procedure to lock a package is simple:

Open synaptic (System > Admin > Synaptic) then search for the package in question. In this case, wpasupplicant, in the search bar. Then, click on it to highlight it in the pane and go Package Menu > Lock version. Then apply. This should solve the problem, you can process all future updates.

I'd like to note that it's better to get the actual problem fixed however. Can you post more details on your situation, more = better. The details of your network for instance? The exact network hardware your using (router and NICs in machines)? I don't run on any broadcom cards at home so can't help much more unfortunately. Post it anyway, and hopefully a more experienced wireless user can give assistance.

Best of luck.

---

### Post by dArAzAc on 2009-06-28
> **starcraft.man said:**
> Do you know exactly which packages you installed that broke your wireless support? 

I'm gonna go out on a limb though and guess that the only two packages that could have caused this trouble would be network-manager and/or wpasupplicant, and it's probably the latter. One possible solution (though not ideal by any means) is to do a vanilla install and then lock the version of wpasupplicant so that it never updates.

Can you post more details on your situation, more = better. The details of your network for instance? The exact network hardware your using (router and NICs in machines)? I don't run on any broadcom cards at home so can't help much more unfortunately. Post it anyway, and hopefully a more experienced wireless user can give assistance.


I'm not sure which updates broke it as a had a slew of them to add post-install. I tried this again, but this time locking wpasupplicant and network-manager (as to your suggestion. The same thing happened. 

Here are some things that may help you help me. Let me know if there is any other info that I can provide.

Diagnoses: Ubuntu seems to fail to recognize my Wifi Card. When I select the network manager tray icon it reads: ```
**Wireless Networks** wireless is disabled
``` 
[INDENT]There is also an option to manage a VPN connection(?)
[/INDENT] Wifi Card: 
```
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:24:e8:a3:18:e2  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fea3:18e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1144931 (1.1 MB)  TX bytes:255088 (255.0 KB)
          Interrupt:248 

eth1      Link encap:Ethernet  HWaddr 00:22:5f:a2:4d:f7  
          inet6 addr: fe80::222:5fff:fea2:4df7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

```

---

