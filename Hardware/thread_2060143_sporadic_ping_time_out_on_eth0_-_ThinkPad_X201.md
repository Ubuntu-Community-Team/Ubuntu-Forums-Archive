---
title: "sporadic ping time out on eth0 - ThinkPad X201"
date: 2012-09-19
forum: Hardware
---

### Post by schroedingerscatisdead on 2012-09-19
Hi Ubuntu users out there. 

I'm really at a miss trying to identify an issue that has come up with my recent updated Ubuntu 12.04 32 bit system that runs on a Lenovo Thinkpad X201. For 2 days I seem to have a very sporadically working ethernet link (Intel Pro 1000 (e1000e driver), Intel 85877 I think). 

By running a continuous ping on e.g. google, I have determined that it only occurs when I use the ethernet connection. Unfortunately dmesg doesn't really reveal any further details on the issue (not even that the link got dropped, and gnome actually still shows that it's being connected. However, ping just freezes (and any attempt on browsing a website results in a timeout). 

I tried updating the installed driver version with one I had found on the intel website - with no success. 

I am worried that this might be a hardware issue but I am really at a miss in how to diagnose this. From what I can tell, this issue almost immediately arises within 5 minutes after activating the adapter (e.g. through the gnome menu or command line). That being said - if I deactivate and re-activate the interface, the link works normal again - for about 3-5 minutes (non deterministic)

I realize that it's probably really difficult to diagnose this without further information on my system, so please tell me if you need more details. 

ethtool -i eth0
driver: e1000e
version: 1.5.1-k
firmware-version: 0.12-1
bus-info: 0000:00:19.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes

At this point the only thing I could think doing would be to re-format the system and cross my fingers that the issues will be gone. But I would *really* appreciate not doing this. 

Thank you very much for your attention and help in resolving this issue!

Thanks!

---

### Post by einonm on 2012-09-19
A few things spring to mind -

*Does eth0 have a fixed IP address or is it allocated via DHCP? There may be a duplicate IP address on your LAN (not very likely though).

* Try pinging a local address instead of google (such as your router or modem). This then eliminates you ISP or an issue outside of your LAN.

* are there any other active network interfaces on your laptop? Try running 'ifconfig' from the command line, and post the results.

---

### Post by schroedingerscatisdead on 2012-09-19
Hi and thanks for your response,

* eth0 is allocated via DHCP but we use a mac registry so I should get the same IP address every time

* aside from eth0 there's of course wifi:

eth0      Link encap:Ethernet  HWaddr XXXXXXXXXXX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:106968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46389928 (46.3 MB)  TX bytes:4186271 (4.1 MB)
          Interrupt:20 Memory:f2500000-f2520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21915 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2093204 (2.0 MB)  TX bytes:2093204 (2.0 MB)

wlan0     Link encap:Ethernet  HWaddr XXXXXXXX  
          inet addr:XXXXX  Bcast:XXXX  Mask:255.255.255.0
          inet6 addr: XXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:183919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150715555 (150.7 MB)  TX bytes:21975304 (21.9 MB)

I have replaced the critical addresses (IP, subnet, Mac) by XXX

* I'll try the ping of the local host tomorrow -- thanks for now!

---

### Post by schroedingerscatisdead on 2012-09-21
Hi again.
So it turns out that it's likely related to routing tables on our corporate network - which is going to make it more difficult. I was able to ping our router but when trying to reach some external address, e.g. google.com, it showed the aforementioned symptoms. 

Thanks I think you may have helped to pin down the issue!

---

### Post by einonm on 2012-09-21
That sounds reasonable. So I guess your laptop is fine and healthy. 

Can the thread get marked as solved? :)

---

### Post by schroedingerscatisdead on 2012-09-22
Hi, 
thanks so much for helping me to narrow down this issue. After talking with our network administrator, it turns out that I got the same IP address assigned based on my MAC. However, a closer look revealed that the service that was taking care of had "lost" my MAC address. This is now fixed. Thanks a lot.

Cheers ):P

---

