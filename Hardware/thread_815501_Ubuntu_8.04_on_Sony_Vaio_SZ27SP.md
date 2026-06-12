---
title: "Ubuntu 8.04 on Sony Vaio SZ27SP"
date: 2008-06-01
forum: Hardware
---

### Post by weiszard on 2008-06-01
I've just installed Ubuntu on to this laptop. The wired connection is working fine. but i cannot seem to configure the wireless. 

I've 2 question;

How do i install the Nvidia driver for my Gforce Fx Go7400?

The network tools is picking up my Wireless card, running lspci shows,

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 15)

ran ifconfig

klaukaikul@Vaio-UBUNTU:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:4a:f7:24:11  
          inet addr:192.168.1.192  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:4aff:fef7:2411/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1936 (1.8 KB)  TX bytes:6844 (6.6 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78800 (76.9 KB)  TX bytes:78800 (76.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:97:c6:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-97-C6-AC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ran iwconfig

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The router is definitely on. my PSP is connected to it. It is configured as DHCP.

what i can think of is a bug in the driver, but how do i sort it out?

---

### Post by hotweiss on 2008-06-01
Try enabling your wifi with a switch or button, it might be an ACPI issue.

---

### Post by weiszard on 2008-06-01
the wifi switch is enabled.

---

### Post by hotweiss on 2008-06-01
I don't know what to tell you at this moment. The wifi card that you have is supported by default. Try Mint, it's based on Ubuntu:

[http://linuxmint.com/mirrors.php?id=25](http://linuxmint.com/mirrors.php?id=25)

See if the wifi will work in a live session.

---

