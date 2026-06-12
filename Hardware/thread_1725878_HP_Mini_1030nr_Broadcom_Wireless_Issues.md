---
title: "HP Mini 1030nr Broadcom Wireless Issues"
date: 2011-04-10
forum: Hardware
---

### Post by kevinvugs on 2011-04-10
I have followed the [http://wireless.kernel.org/en/users/Drivers/b43#support](http://wireless.kernel.org/en/users/Drivers/b43#support)
tutorial to letter for my particular broadcom chipset and I still am not able to get it to work... 

Ubunutu 10.10 netbook remix

the output of  lspci -vnn | grep 14e4    

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [[14e4:4315] (rev 01)   and the 14e4 is in red

any help would be greatly appreciated...

---

### Post by mikewhatever on 2011-04-10
So what doesn't work exactly? Can you see the networks around you?
Can you post the outputs of the following:
```

ifconfig
lsmod | grep b43

```

---

### Post by kevinvugs on 2011-04-10
ifconfig - eth0      Link encap:Ethernet  HWaddr 00:24:81:46:d1:17  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe46:d117/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2099 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1964796 (1.9 MB)  TX bytes:351762 (351.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

and lsmod | grep b43 

[COLOR=Red]b43  [/COLOR]                 168681  0 
mac80211                  231959  1 [COLOR=Red]b43[/COLOR]
cfg80211                  144694  2 [COLOR=Red]b43[/COLOR],mac80211
led_class                  2633  1 [COLOR=Red]b43[/COLOR]
ssb                       39320  1 [COLOR=Red]b43

[COLOR=Black]no it says the wireless is disabled [/COLOR]
[/COLOR]

---

### Post by mikewhatever on 2011-04-10
It looks like the interface is down. If there is a switch to turn it on try that, and if there isn't:
```
sudo ifconfig wlan0 up
```

---

### Post by kevinvugs on 2011-04-10
SIOCSIFFLAGS: Operation not possible due to RF-kill

So I did...

rfkill list

0: phy0: Wireless LAN
        Soft blocked: no 
        Hard blocked: yes
1: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

so I did...

sudo rfkill unblock 0
sudo rfkill unblock 1

and ifconfig now

eth0      Link encap:Ethernet  HWaddr 00:24:81:46:d1:17  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe46:d117/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1382231 (1.3 MB)  TX bytes:231433 (231.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:ab:6a:a4  
          inet6 addr: fe80::224:2bff:feab:6aa4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3279 (3.2 KB)

lsmod | grep b43 nothing has changed

physical switch is on and lit up blue which seems to be a good sign and I can see my network but it still won't hook up wireless... and I have tried to install the propietary driver under the additional drives and it gives me the systemerror: InstallArchives()failed

---

### Post by mikewhatever on 2011-04-10
Perhaps you'll have better luck with the STA broadcom driver? Get it with installing the bcmwl-kernel-source package, but obviously, remove the b43-fwcutter before that.

---

### Post by kevinvugs on 2011-04-11
I did try the STA and it gave the same error message. But here is what I did. Fresh install of Maverick 10.10 with the updates being installed along with the OS installation. Full update from update manager. Restart and then used the additional drivers package to install the STA driver and that was successful. Thank you for the response.

---

