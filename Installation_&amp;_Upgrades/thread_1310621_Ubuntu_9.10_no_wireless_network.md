---
title: "Ubuntu 9.10 no wireless network"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2009-11-01
Please can anybody give me a hand?

I just installed Ubuntu 9.10 and I'm now not able to use internet.

```

jiapei@jiapei-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Tiscali12D18F"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on



jiapei@jiapei-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:d0:a9:19:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:7c:1b:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



jiapei@jiapei-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


jiapei@jiapei-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:7c:1b:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:aa100000-aa100fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:09:08.0
       logical name: eth0
       version: 02
       serial: 00:40:d0:a9:19:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:a4000000-a4000fff ioport:1200(size=64)


```

Looking forward to your reply.

Best Regards
JIA

---

### Post by jiapei100 on 2009-11-02
Tried booting directly by the burn Ubuntu 9.10 CD, problem continues.

I seems that Ubuntu 9.10 was not willing to connect the wireless network at all.

So, can anybody please help? please !!

Best Regards
JIA

---

### Post by wilee-nilee on 2009-11-02
Not being a person who likes modifying files if you can hard plug to get on the net install wicd it is a good replacement.

---

### Post by jiapei100 on 2009-11-02
Tested already.

It seems there is nothing to do with wicd or network-manager....

I'm now using wicd and "no wireless network found" is just up there in the wicd window.

I'm guessing whether it has something to do with the network card driver?





> **wilee-nilee said:**
> Not being a person who likes modifying files if you can hard plug to get on the net install wicd it is a good replacement.

---

### Post by flaflashr on 2009-11-21
I don't know if this will help your problem or not, but it just solved mine. Kubuntu 9.10 Krusty Klown new installation on Dell D400 with Broadcom set trying to connect wifi, but Wicd kept reporting "No wireless network found" (I used Wicd because of previous errors on other machines trying to use the KDE Network Mangler).

lshw -C network reported *-network DISABLED

Solution was to to go to Applications | System | Hardware Drivers which reported "No proprietary drivers ...", but also listed Broadcom B43 Wireless Driver, tested by Ubuntu Developers, License Free. At bottom of this dialog, "This drivers is not currently activated". I clicked the activate button, and it downloaded and installed the driver, and my Wifi network was magically found.

The dialog box also mentions "fwcutter is a tool which can extract firmware from various source files. It's written for BCM43xx driver files."

Hope that somebody finds this helpful.

JimR

---

