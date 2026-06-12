---
title: "Built-in Ethernet Card not Working"
date: 2010-01-04
forum: Hardware
---

### Post by beagler on 2010-01-04
Here's My Story:

About 8 hours ago I reformatted an old machine with Ubuntu 9.10 with the intent of using it as a media center thing behind my T.V. 

Previously, I used it as a cheap webserver and it had Ubuntu 7.x or 8.x on it, I cant really remember. 

Anyways, the ethernet card used to work fine and now it does not. I've never had an issue with wired connections in ubuntu before and I have no idea how to fix this. When I first boot, it tries to connect for a while and then tells me "Disconnected from network,"  or something to that degree.

Here is some output which might help someone help me:
(i would really appreciate it)

```
andy@andy-media-center:~$ sudo lshw
[sudo] password for andy: 
andy-media-center         
    description: Desktop Computer
    product: A13G
    vendor: PCCHIPS
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
[...]
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1b:b9:cd:60:5a
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:27 memory:fe02d000-fe02dfff ioport:ec00(size=8)
[...]
    
andy@andy-media-center:~$ ethtool -i eth0
driver: forcedeth
version: 0.64
firmware-version: 
bus-info: 0000:00:07.0

andy@andy-media-center:~$ sudo ethtool -t  eth0
The test result is PASS
The test extra info:
link      (online/offline)	 0
register  (offline)       	 0
interrupt (offline)       	 0
loopback  (offline)       	 0

andy@andy-media-center:~$ ping www.google.com
ping: unknown host www.google.com


andy@andy-media-center:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:cd:60:5a  
          inet6 addr: fe80::21b:b9ff:fecd:605a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:204381 (204.3 KB)  TX bytes:5456 (5.4 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

---

### Post by iponeverything on 2010-01-04
From everything you posted, it looks like your your card is fine.

So, before was the machine set up with a static IP? Is there DHCP server running somewhere on the network to hand out an IP to machine?

If there is, are there is a DHCP server, is it setup just to had out IP addresses to based on MAC? 

install tcpdump from install CD and run it with:

```
sudo tcpdump -i eth0 >> ~/Desktop/tcpdump-output.txt 2>&1

```

Let it run while the machine is trying to connect and for about 10 minutes after.. then upload the file. It might give an idea of what is going on. The output of your ifconfig had over 200k of rx traffic on that interface, so something is floating around..

---

### Post by beagler on 2010-01-04
Hey. Thanks so much for the help, It was quite helpful. I'm not really sure what I did to fix it, but it works now. I had just finished doing that tcpdump and was about to upload the results when I decided to try rebooting once more and it went ahead and worked.

It used to be set up so that the router would give a static IP to this mac address, but now its just going straight through a different modem with no router at all so that couldnt have been an issue. 

Anyways, thanks. Im super stoked that my hours of fiddling finally worked.

---

