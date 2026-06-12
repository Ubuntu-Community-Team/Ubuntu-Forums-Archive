---
title: "no network connection"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by GGTutor on 2009-10-24
Hi, I am completely new to linux but would like to try it and maybe dump XP, but first I need to get it working. I have installed 9.04 and seems to be working, but I am having a problem accessing the internet. Ihave  tried a full install (dual boot with XP) and Wubi on XP and the live CD. Sometimes, although rarely, I get a connection on eth1 which implies the hardware will work, and it is working fully on XP.

I would like to give Ubuntu a try, but without internet this will be tough to say the least.

I am using an ASUS P5Q-E motherboard which according to the forum is compatible.

Any help at all would be greatly appreciated.

Thanks

---

### Post by rampageoberon on 2009-10-24
Hi there,

I use the Asus P5Q motherboard, and I had some trouble recognising the onboard network card. Is this the same thing causing you problems or something else?

Maybe the below links may help.
[http://ubuntuforums.org/showthread.php?t=770173&highlight=l1e-linux](http://ubuntuforums.org/showthread.php?t=770173&highlight=l1e-linux)
[http://ubuntuforums.org/showpost.php?p=5456722&postcount=19](http://ubuntuforums.org/showpost.php?p=5456722&postcount=19)
[http://ubuntuforums.org/showpost.php?p=5568394&postcount=29](http://ubuntuforums.org/showpost.php?p=5568394&postcount=29)

---

### Post by GGTutor on 2009-10-24
HiaAs I said I am completely new to linux and wouldn't know how to detect the problem. I tried  lspci and the ethernet controller comes up and eth0 and eth1 are detected, but no connection, and then sometimes for no reason it connects. I don't know where to start looking to try and fix it.

Thanks a lot for the pointers, I will take a look.

---

### Post by rampageoberon on 2009-10-24
What is the ethernet controller when you do lspci?

---

### Post by GGTutor on 2009-10-24
the controller is 
marvell technology 88E8056 PCI-E

---

### Post by rampageoberon on 2009-10-24
Okay, so its not the same problem I had. Not sure exactly what it could be, but could you please post the output of the following:
```
sudo lshw -C network
ifconfig
```

Cheers

---

### Post by GGTutor on 2009-10-24
it will take me a while because I am on XP now, will have to reboot to live cd and then back into XP to post using internet. I will get it up as quick as possible.

---

### Post by GGTutor on 2009-10-24
ok here we go

```
**lshw -C network**
ubuntu@ubuntu:~$ sudo lshw -C network
  
*-network               
       
description: Ethernet interface
       
product: 88E8056 PCI-E Gigabit Ethernet Controller
       
vendor: Marvell Technology Group Ltd.
       
physical id: 0
       
bus info: pci@0000:02:00.0
       
logical name: eth0
       
version: 12
       
serial: 00:22:15:8f:30:37
       
capacity: 1GB/s
       
width: 64 bits
       clock: 33MHz
       
capabilities: pm vpd msi pciexpress bus_master cap_list 
ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no 
module=sky2 multicast=yes port=twisted pair
  

*-network:0
       
description: Wireless interface
       
product: ACX 111 54Mbps Wireless Interface
       
vendor: Texas Instruments
       
physical id: 0
       
bus info: pci@0000:05:00.0
       
logical name: wlan0
       
version: 00
       
serial: 00:0f:b5:48:43:e5
       
width: 32 bits
       clock: 33MHz
       
capabilities: pm bus_master cap_list ethernet physical wireless
       
configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+
  

*-network:1
       
description: Ethernet interface
       
product: 88E8001 Gigabit Ethernet Controller
       
vendor: Marvell Technology Group Ltd.
       
physical id: 2
       
bus info: pci@0000:05:02.0
       
logical name: eth1
       
version: 14
       serial: 00:22:15:8f:46:67
       
size: 100MB/s
       capacity: 1GB/s
       
width: 32 bits
       clock: 66MHz
       
capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       
configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full 
firmware=N/A latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
  

*-network DISABLED
       
description: Ethernet interface
       
physical id: 1
       
logical name: pan0
       
serial: de:f8:65:da:77:4c
       
capabilities: ethernet physical
       
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


**ifconfig**

eth0      
Link encap:Ethernet  HWaddr 00xxxxx  
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          
Interrupt:17 



eth1      
Link encap:Ethernet  HWaddr 00xxxxx  
          
inet6 addr: fe80::222:15ff:fe8f:4667/64 Scope:Link
          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
RX packets:245 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:16243 (16.2 KB)  TX bytes:492 (492.0 B)
          
Interrupt:18 



lo        
Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:1460 (1.4 KB)  TX bytes:1460 (1.4 KB)



wlan0     
Link encap:Ethernet  HWaddr 00xxxxx  
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          
Interrupt:16 Base address:0xe000 
```





I notice that it says network DISABLED, I guess this is the problem.


cheers

---

### Post by rampageoberon on 2009-10-24
Hmm, okay so you have 2 ethernet interfaces (eth0 and eth1). I'm not exactly sure what the problem could be, but from the ifconfig command it looks to me like the MAC address is not showing correctly. Maybe someone else viewing this will know better.

I also assume that you are connected to eth1, so try do the following

```
sudo ifconfig eth1 down
sudo ifconfig eth1 hw ether 00:22:15:8f:46:67
sudo ifconfig eth1 up
```

I hope this helps. Also post the output of "ifconfig eth1" to see if it makes any difference.

---

### Post by GGTutor on 2009-10-24
Thanks for the help, it is getting a bit late here and I need to eat, I've been trying to solve this all day:confused:. I will post the items you mentioned later and see what comes of that. I don't give up easily:).


Found this bug report that isn't very encouraging [URL="https://answers.launchpad.net/ubuntu/+source/linux/+question/78730"]https://answers.launchpad.net/ubuntu/+source/linux/+question/78730
[/URL]
Thank you very much for your time.

Cheers.

---

### Post by rampageoberon on 2009-10-24
Sorry haven't managed more today. I'm sure with the help of the community you'll get a solution.

And excellent attitude and approach you have :)

---

### Post by GGTutor on 2009-10-25
I am new to linux and have been trying to install 9.04 for the last 3 days, I am close to giving up now.](*,) I got everything working on the live cd and then installed to a separate drive to dual boot with xp. Everything worked fine:P. I then updated and found that I had no network connection, so I have spent ages trying to find solutions, no luck as my ASUS P5Q-E seems compatible and nobody else seems to have the same problem.

So, I went back to the live CD and found that this now also cannot connect, when it could before:confused:. Anyway, to cut a long story short and after reinstalling several times, I think I have found the problem.

After updating I am offered two kernels to boot from 2.6.28.16 or 2.6.28.11 (the one on live cd) If I boot into 2.6.28.16 I get this error on a black screen when shutting down

>nm-system-settings: SCPlugin-ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_
>nm-system-settings: SCPlugin-ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_


and have to press the power button to reset. On rebooting I can no longer get a network, this includes from the live cd. If I boot into 2.6.28.11 (without having booted into 2.6.28.16), I get a network but the system is now incredibly slow and eventually crashes.:(


I am afraid with my limited knowledge of linux I haven't a clue where to start now. Can anyone help me, I'd really like to try ubuntu out even though my first steps haven't been encouraging.


Cheers

---

### Post by GGTutor on 2009-10-25
I found this bug report, but don't really know what I should do now.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/357578](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/357578)

anyone got any ideas?

---

### Post by GGTutor on 2009-10-25
after further investigation I have moved this to a new thread

[http://ubuntuforums.org/showthread.php?t=1300730](http://ubuntuforums.org/showthread.php?t=1300730)

---

### Post by GGTutor on 2009-10-25
Anyone know if this is a bug or not? At least I can know whether to give up then.

thanks

---

### Post by GGTutor on 2009-10-25
Did I say something wrong?:confused:

---

### Post by Iowan on 2009-10-25
Since the other thread doesn't seem to have much response, I'll use this one... 
Are you using Network Manager to configure the interface(s)? Are you connecting to eth0 or eth1? What, (if anything) is connected to the other one? NM only manages one interface at a time.  
Please post results of **ifconfig -a**.

---

### Post by cariboo on 2009-10-25
> **GGTutor said:**
> I found this bug report, but don't really know what I should do now.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/357578](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/357578)

anyone got any ideas?

This bug has nothing to do with your problem, the error they are talking about showed up at shutdown.

Have you tried disabling one of your nics in the bios, then see if you still have the same problem?

**Note**:I merged the two threads, so there is no confusion.

---

### Post by GGTutor on 2009-10-26
Firstly, can I apologise if I broke any forum protocol by posting in twice, my frustration and impatience got the best of me:oops:

Thank you for you replies and now with a cooler head I seem to have got somewhere. The errors on shutdown no longer appear with a couple of reboots in recovery mode, I don't know what the problem was but I can now start and shutdown with no problems :p.

I still have network problems though, I have manually entered IP/Subnet/Gateway in network manager and it now tells me I have a network connection, but when I load firefox I can't get anything:confused:.

I am using Comtrend Powerline Ethernet connectors to connect to my BT Home Hub through eth0. In windows the powerline connectors don't prevent me connecting, might they do so in Ubuntu?

I will post her ifconig -a as requested and also some warnings I saw in Daemon log (athough I have no idea if this is relevant or useful to anyone:o)

```
ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:22:15:8f:30:37
  
        inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
 
         inet6 addr: fe80::222:15ff:fe8f:3037/64 Scope:Link
 
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
 
         RX packets:132 errors:0 dropped:0 overruns:0 frame:0
 
         TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
 
         collisions:0 txqueuelen:1000 
          RX bytes:8087 (8.0 KB) 
         TX bytes:5924 (5.9 KB)
          Interrupt:17 



eth1      Link encap:Ethernet  HWaddr 00:22:15:8f:46:67 
 
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



pan0      Link encap:Ethernet  HWaddr 46:38:1c:48:bd:da 
 
          BROADCAST MULTICAST  MTU:1500  Metric:1
 
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 
         collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:48:43:e5  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1
   
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 
         collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:16 Base address:0xe000 


```
daemon log warning

```
Oct 26 22:44:14 darren-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 

Oct 26 22:44:14 darren-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 

Oct 26 22:44:33 darren-desktop NetworkManager: <WARN>  nm_error_monitoring_device_link_state(): error monitoring device for netlink events: error occurred while waiting for data on socket  

Oct 26 22:44:46 darren-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 

Oct 26 22:44:46 darren-desktop NetworkManager: <info>    address 192.168.1.71 

Oct 26 22:44:46 darren-desktop NetworkManager: <info>    prefix 24 (255.255.255.0) 

Oct 26 22:44:46 darren-desktop NetworkManager: <info>    gateway 192.168.1.254 

Oct 26 22:44:46 darren-desktop NetworkManager: <info>    nameserver '192.168.1.254' 

Oct 26 22:44:46 darren-desktop NetworkManager: <info>    domain name 'home' 

Oct 26 22:44:46 darren-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 

Oct 26 22:44:46 darren-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 

Oct 26 22:44:46 darren-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 

Oct 26 22:44:46 darren-desktop avahi-daemon[2979]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.71.

Oct 26 22:44:46 darren-desktop avahi-daemon[2979]: New relevant interface eth0.IPv4 for mDNS.

Oct 26 22:44:46 darren-desktop avahi-daemon[2979]: Registering new address record for 192.168.1.71 on eth0.IPv4.

Oct 26 22:44:47 darren-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 

Oct 26 22:44:47 darren-desktop NetworkManager: <info>  Policy set 'eth0' (eth0) as default for routing and DNS. 

Oct 26 22:44:47 darren-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 

Oct 26 22:44:47 darren-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 

Oct 26 22:44:57 darren-desktop NetworkManager: <WARN>  nm_error_monitoring_device_link_state(): error monitoring device for netlink events: error occurred while waiting for data on socket  

Oct 26 22:48:06 darren-desktop ntpdate[3551]: step time server 91.189.94.4 offset 0.512437 sec

Oct 26 22:49:08 darren-desktop NetworkManager: <WARN>  nm_error_monitoring_device_link_state(): error monitoring device for netlink events: error occurred while waiting for data on socket  

Oct 26 22:50:31 darren-desktop NetworkManager: <WARN>  nm_error_monitoring_device_link_state(): error monitoring device for netlink events: error occurred while waiting for data on socket  


```
I am not sure what else I can post, just let me know.


Thank you once again.

---

### Post by drspiff on 2009-10-26
Nevermind... my net problem with 8.0.4 has mystically, magically resolved itself. If it crops up again, I'll post.

Thanks,
Rick

---

### Post by Iowan on 2009-10-26
The router is at 192.168.1.254? Can you **ping** it (from a terminal)?  If so, try **ping**-ing an internet address (like 74.125.67.100). If that works, the DNS may need "adjusting".

---

### Post by GGTutor on 2009-10-27
Thanks for your help Iowen, I'm struggling on here, but in a perverse way enjoying trying to solve this.

Anyway, came hometonight booted up and no connection on network manager even though it said connected last night with manual settings. I am not sure I entered them correctly as I haven't had to do it before. So set network manager back to dhcp to start again. I got these settings off of my xp installation on the same machine.

ip 192.168.1.71
subnet 255.255.255.0
gateway 192.168.1.254

these are what i entered but no luck.

So as of now network manager reports no connection ethernet or wireless. I will repost my ifconfig -a whennetwork manager is set to dhcp

```
fconfig -a

eth0      Link encap:Ethernet  HWaddr 00:22:15:8f:30:37 
 
          inet6 addr: fe80::222:15ff:fe8f:3037/64 Scope:Link
 
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
  
        RX packets:17 errors:0 dropped:0 overruns:0 frame:0
   
       TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
  
        collisions:0 txqueuelen:1000 
 
         RX bytes:1306 (1.3 KB)  TX bytes:4553 (4.5 KB)
 
         Interrupt:17


eth1      Link encap:Ethernet  HWaddr 00:22:15:8f:46:67 
 
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
 
         RX packets:68 errors:0 dropped:0 overruns:0 frame:0
 
         TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
 
         collisions:0 txqueuelen:0 

          RX bytes:5200 (5.2 KB)  TX bytes:5200 (5.2 KB)




pan0      Link encap:Ethernet  HWaddr fa:cf:66:e6:9b:2f 
 
          BROADCAST MULTICAST  MTU:1500  Metric:1
  
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
  
        collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:48:43:e5 
 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
  
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
   
       collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
         Interrupt:16 Base address:0xe000 


```


Are there any suggestions as to what I can do now as I am truly stuck. I also notice that if I leave the machine for a while it freezes and I have to reset from the power button, but this may be another problem. Perhaps I should wait a couple of days and try 9.10.

Thanks in advance.

---

### Post by Iowan on 2009-10-27
:confused: Is machine currently set to DHCP or with address 192.168.1.71?
Have you seen/tried [this]("http://ubuntuforums.org/showthread.php?t=1156441") one? (Doubt it'll help, but you never know...)

---

### Post by GGTutor on 2009-10-27
sorry didn't make myself clear, I put back to dhcp because not confident in my ability to set up manually. I will try your suggestion tomorrow, getting late here.

previous ifconfig -a is when set at dhcp in network manager


Thanks again;)

---

### Post by GGTutor on 2009-10-28
Ok tried again tonight #-o. I tried the suggestion made by Iowen in earlier post but didn't seem to make any difference, so I put it back how it was. Thank you for the suggestion Iowen, I appreciate you sticking with me on this one:D.

I entered manual settings again and am now able to ping my router and can get my router's front page up in firefox. However, it is unbelievably slow and if I try to explore other pages on the router's settings page it times out. I cannot get internet at all, nothing. If I ping [www.google.com](www.google.com) it says host unknown.

I really can't tell if I am getting somewhere or not, I have spent about 7 evenings now trying to get connected, I am starting to lose hope. I see a lot of posts for troubleshooting wireless but not wired (I guess it normally works). Can anyone link me a guide to troubleshooting wired networks for beginners?

Thanks in advance

---

### Post by Iowan on 2009-10-28
Sounds like DNS is still not happy. What is in */etc/resolv.conf*? It *should* be your nameserver(s). You could try OpenDNS (208.67.222.222 and 208.67.220.220). Sometimes Network Manager overwrites this one anyway.

---

### Post by GGTutor on 2009-10-29
Iowan, I cannot thank you enough!! I checked /etc/resolv.conf and found no entries, took my DNS from XP and placed it in, reboot and I now have fully working internet\\:D/, and fast too. I disabled the wireless network card which seems to be clashing and slowing it down too (may seem obvious to some, but not me).

Anyway,** thank you** again Iowan you have stuck with me in my ignorance and patiently helped me solve a problem I couldn't have fixed alone.

 Hope I can now learn enough to do the same for someone else one day;)

---

