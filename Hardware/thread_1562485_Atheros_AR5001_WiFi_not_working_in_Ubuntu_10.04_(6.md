---
title: "Atheros AR5001 WiFi not working in Ubuntu 10.04 (64 bit)"
date: 2010-08-27
forum: Hardware
---

### Post by pirx82 on 2010-08-27
Hi everyone,

I'm using a Lenovo R500 laptop with Ubuntu 10.04 LTS (64 bit). Everything seems to work fine, except for the WiFi card.

This card was in Windows 7 recognized as "**11 b/g/n Wireless LAN Mini PCI express Adapter II**." As far as I was able to determine, Lenovo branded two types of WiFi cards by this name. One was **Realtek 8172 or 8192SE** and the other was **Atheros AR5001**. If I got it right, mine is Atheros AR5001.

I have found a tutorial on how to install this card here: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

As suggested, I enabled the Backports repository by adding it to the /etc/apt/sources.list. I guess that it works, because when I checked for updates with "Update Manager", there were updates available from Backports. However, I wasn't able to find the **ath5k** module.

I would be very grateful if someone could explain to me how to find and add the ath5k module.

Thank you and best regards!

---

### Post by pirx82 on 2010-08-28
Hi again,

I'm still trying to enable my WiFI, but with no success. Any help would be *much* appreciated! :)

---

### Post by pirx82 on 2010-08-29
Hello,

I've found some useful information on this thread: [http://www.uluga.ubuntuforums.org/showthread.php?t=1383366](http://www.uluga.ubuntuforums.org/showthread.php?t=1383366)

My laptop also doesn't recognize the WiFi card and "karg" solved this issue by installing the "**compat-wireless**". 

In Synapric Package Manager I am able to find the compat-wireless, but there are several versions of it:
- compat-wireless Linux modules for version 2.6.32 on x86/x86_64 (generic)
- compat-wireless Linux modules for version 2.6.32 on x86/x86_64 (preempt)
- compat-wireless Linux modules for version 2.6.32 on x86/x86_64 (server)

Does anyone know if I need to install all packages? I really don't want to mess up my system. :) Thanks!

---

### Post by varunendra on 2010-08-30
As far as I know, you can always roll back any module safely, without leaving a trace, as long as it hasn't removed any previously existing modules to upgrade with new ones. Having said that, it seems the '**generic**' one should be for you. Other two shouldn't be needed.

By the way, how did you determine that your card is Atheros and not realtek?

If you are not absolutely sure about it, please post the output of:
```
sudo lshw -C network
```Also, see if this returns some results:
```
dmesg | grep wireless
*or*
dmesg | grep wlan0
```

---

### Post by pirx82 on 2010-08-30
Hi, varunedra!

Thank you for your reply.

The output of "**sudo lshw -C network**" is this:

```
*-network       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4e:d4:6f:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.32-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f4300000-f430ffff

```

Command "**dmesg | grep wireless**" doesn't show anything (as if the system would ignore it) and "**dmesg | grep wlan0**" returns this:

```
[   19.044706] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  106.273803] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[16830.453818] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```Your help is much appreciated!

---

### Post by varunendra on 2010-08-30
Well, let's first make it clear that I'm not an expert in these Wifi issues, nor do I have access to any system with Wifi. So I'm certainly not the right person for you.

However, I'll try to help with whatever I've learnt through experience of others so far.

Evidently, you are right about your card being Atheros. It also seems to be detected correctly by the kernel (no errors except "link not ready"!). Hence I wonder if there may be only configuration issue. So before trying anything complex, let's check these first:

**1)** Outputs of:
```
ifconfig -a
``````
iwconfig
```**2)** Is the problem that you are unable to even switch on the Wifi? (just confirmation)
**3) **Are you able to connect via ethernet?

Last, if you haven't already noticed, ath5k module is already in use for your card (see 2nd last line in the first output). So maybe we need something else (or maybe just a little configuration??)


**_PS_:**
Also, check if there's any 'Hotkey' on your laptop to turn on the Wifi as suggested [here]("http://ubuntuforums.org/showpost.php?p=9784330&postcount=3").

---

### Post by pirx82 on 2010-08-30
Hi again,

er... sorry for me being stupid. :) The WiFi works now! Because the LED indicator for WiFi was off, I never thought of disconnecting the UTP cable. Well, just out of curiosity, I have disconnected it and voila! My router was recognized and I was able to connect to it using WPA. Man, how could I know? Windows wasn't working like this. No LED mean't no WiFi!

Anyway, here are the outputs:

```
eth0      Link encap:Ethernet  HWaddr 00:1c:25:9c:ee:5c  
          inet6 addr: fe80::21c:25ff:fe9c:ee5c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12924486 (12.9 MB)  TX bytes:978640 (978.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18272 (18.2 KB)  TX bytes:18272 (18.2 KB)

pan0      Link encap:Ethernet  HWaddr 8a:f0:81:c6:b9:63  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:4e:d4:6f:30  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4eff:fed4:6f30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105503 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:259518909 (259.5 MB)  TX bytes:9354007 (9.3 MB)
```

and

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"K35Router"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: E0:CB:4E:E4:B3:16   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

```

Thanks again for your kind help.

---

### Post by varunendra on 2010-08-30
:|Do you really think I still need these?:|


:lolflag:

---

### Post by pirx82 on 2010-08-30
No, but I posted them anyway just in case, if something fishy would be hiding there. :D

---

