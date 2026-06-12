---
title: "Using 8.10 Wireless drivers Issue -- Broadcom"
date: 2008-11-17
forum: General Help
---

### Post by Titan8990 on 2008-11-17
I recently reformatted by Ubuntu box because I needed to try some backup server software called Restore-EE that only had repositories for 7.10 and earlier (yes, I tried them on 8.10). 


So anyways after my testing was finished I decided to upgrade to 8.10 again and use the Restricted Hardware Drivers Manager to install my wireless drivers so I did not have to mess with ndiswrapper again. 

The problem is that it turned my Broadcom card in to a eth interface. Eth interfaces don't support scannning. How am I meant to find a wireless network? The network Gnome applet does not appear anymore (most likely because my wireless got named eth2).

Anyone else had this issue an know of a resolution?

Here is some additional information:

```
jordan@bourne:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:73:7a:c3  
          inet addr:192.168.192.18  Bcast:192.168.192.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe73:7ac3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:803264 (803.2 KB)  TX bytes:119604 (119.6 KB)
          Interrupt:20 Base address:0xe000 

eth2      Link encap:Ethernet  HWaddr 00:1a:73:80:59:86  
          inet6 addr: fe80::21a:73ff:fe80:5986/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:1
          TX packets:0 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4100 (4.1 KB)  TX bytes:4100 (4.1 KB)
```

```
jordan@bourne:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.
```


```
jordan@bourne:~$ iwlist eth2 scanning
eth2      Interface doesn't support scanning.

```


Thanks in advance for any help.


Edit:

Also, my username does not appear on the panel with shut down options as it did before. This is not a major issue as I usually shutdown/reboot from the CLI.

---

### Post by phidia on 2008-11-17
This was an upgrade not a clean install? Just wanting to clarify the situation.

Sometimes upgrades will cause some issues-perhaps your situation fits that particularly  since you noticed some unusal shutdown behavior. 

If you want to continue working with the present install you may need to go through the [wireless troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847&highlight=broadcom")

---

### Post by Titan8990 on 2008-11-17
This is a upgrade. I had this issue before when I upgraded but I just uninstalled the new drivers that Ubuntu had provided and my ndiswrapper drivers were still there. 

That troubleshooting guide seems to assume that your drivers are installed via ndiswrapper.

I can't understand at all why it would make my wireless interface an eth interface....

It looks like I am just going call the Ubuntu wireless drivers "broken" and go back to ndiswrapper that I know works.

---

### Post by Titan8990 on 2008-11-17
Sorry about the double post but do you know if there is a way to just change the "logical name" of a device?

```
jordan@bourne:~$ sudo lshw -C Network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 02
       serial: 00:1a:73:80:59:86
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

```

---

### Post by Titan8990 on 2008-11-17
Another update: 

After uninstalling the wireless driver from the Restricted Drivers Manager by interface is now wlan0.

I still do not have the network applet for gnome and it just connected to the nearest unsecured wireless network (not what I wanted).


Is there a GUI tool for searching and logging on to wireless networks that does not just appear automagically like the Gnome wireless applet?

```
jordan@bourne:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:73:7a:c3  
          inet addr:192.168.192.18  Bcast:192.168.192.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe73:7ac3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4237497 (4.2 MB)  TX bytes:344097 (344.0 KB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4100 (4.1 KB)  TX bytes:4100 (4.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:80:59:86  
          inet6 addr: fe80::21a:73ff:fe80:5986/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:204 (204.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-80-59-86-39-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
jordan@bourne:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Belkin_G_Plus_MIMO_016EFF"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:DF:01:6E:FF   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=61/100  Signal level:-82 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by Titan8990 on 2008-11-18
bump

---

### Post by Titan8990 on 2008-11-18
Update:

I was trying to connect to my AP via the CLI. When I was reading the man page for iwconfig I say that the key argument does not support passphrases??

How can I connect to WPA2 secured AP if iwconfig does not support passphases? 

Am I using the wrong flag? 

Is there any way I can force the gnome wireless applet to appear?

---

### Post by Titan8990 on 2008-11-19
bump, still looking for a way to graphically log on to a wireless network that support WPA2.

---

### Post by Titan8990 on 2008-11-20
up again

---

