---
title: "Wireless internet with CQ40-317TU"
date: 2009-11-15
forum: Hardware
---

### Post by sgk111 on 2009-11-15
I am using Ubuntu 9.10 in Compaq CQ40-317TU laptop.

I would like use Wireless Internet with this. Can someone suggest.

---

### Post by DFlame on 2009-11-15
This supposedly has wireless built in. Are you having trouble using it or detecting networks?

Open a Terminal window and post the output of the following commands here:

```
ifconfig
iwconfig
lshw -C network

```

---

### Post by sgk111 on 2009-11-15
Thank you...

I am sending the reply as per above suggestions...

[COLOR=Orange]sgk@sgk-laptop:~$ ifconfig[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:23:5a:26:a8:b2  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:fe26:a8b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:142767303 (142.7 MB)  TX bytes:6100123 (6.1 MB)
          Interrupt:30 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:21:00:ad:ab:a2  
          inet6 addr: fe80::221:ff:fead:aba2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94392 (94.3 KB)  TX bytes:94392 (94.3 KB)

[COLOR=Orange]sgk@sgk-laptop:~$ iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
[COLOR=Orange]sgk@sgk-laptop:~$ lshw -C network[/COLOR]
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:ad:ab:a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:98500000-98503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:26:a8:b2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.3 latency=0 multicast=yes
       resources: irq:30 ioport:3000(size=256) memory:92410000-92410fff(prefetchable) memory:92400000-9240ffff(prefetchable) memory:92420000-9243ffff(prefetchable)
sgk@sgk-laptop:~$ 



I am a new user to Ubuntu and installed a few days back only.

---

### Post by DFlame on 2009-11-16
Thanks for the info. A little research into the model of your card has yielded this:

```
sudo apt-get install bcmwl-kernel-source
```

Try that command in the terminal, then restart the computer. This worked for [this guy](http://jetpackweb.com/blog/2009/10/29/ubuntu-9-10-karmic-koala-and-broadcom-bcm4312/).

Let us know if there is more trouble!

---

### Post by sgk111 on 2009-11-16
This is the output of your command...

sgk@sgk-laptop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sgk@sgk-laptop:~$

I restarted and tried with wireless network. But not helping.

Thanks.

---

### Post by DFlame on 2009-11-18
It does appear to be running. Lets see if we can detect any networks in Terminal:

```
sudo iwlist eth1 scan
```

Post any errors/output :)

---

### Post by sgk111 on 2009-11-18
This is the output for your command...

[COLOR=Orange]sgk@sgk-laptop:~$ sudo iwlist eth1 scan[/COLOR]
eth1      Scan completed :
          Cell 01 - Address: 00 : 1B : DA : 2E : D4 : 39
                    ESSID:"UTStarcom"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-46 dBm  Noise level:-91 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                                    24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                                    12 Mb/s; 48 Mb/s

[COLOR=Orange]sgk@sgk-laptop:~$ [/COLOR]

---

### Post by DFlame on 2009-11-18
Everything seems to be working perfectly. Is UTStarcom the name of the network you need to connect to?

Failing that, what exactly are you trying to connect to wirelessly?

---

### Post by sgk111 on 2009-11-18
I am simply switching on my Wireless button of laptop. And without having wired connection, trying to access internet.

I am getting failed there. No internet is coming.

UTStarcomm is the modem. (it is WA3002G4).

---

### Post by sgk111 on 2009-11-27
Thank you for spending so much time.
 
Anyway I found out solution.
 
I formatted Ubuntu and installed Windows 7. There are no problems and system works without installation of any drivers. Everything functions well.
 
it is good OS and takes care of many things...
 
Thank you...

---

