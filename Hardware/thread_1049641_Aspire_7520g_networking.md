---
title: "Aspire 7520g networking"
date: 2009-01-24
forum: Hardware
---

### Post by Heme on 2009-01-24
Hello,

Am using the 64bit Hardy Heron and I've never managed to get a wlan to work on this lappy of mine. eth0 connections work flawlessly.

Today I decided to tackle the problem and with some community help (ty, n8tuser) managed to get some progress but there are still some problems.

There's a wireless router that shares the connection to the apartment, ubuntu is assigned an external IP and the nameservers are delivered, yet no connection whatsoever can be made. Cant even ping the router itself. (destination host unreachable)

> heme@heme-laptop:~$ ifconfig; 
eth0      Link encap:Ethernet  HWaddr 00:1b:38:e1:ac:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9432 (9.2 KB)  TX bytes:9432 (9.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:22:2d:64  
          inet addr:192.168.0.139  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e1ff:fe22:2d64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10209 (9.9 KB)  TX bytes:11071 (10.8 KB)
          Interrupt:19 Memory:d0400000-d0410000 

heme@heme-laptop:~$ iwconfig;
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"relacom"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A:65:E3:7B   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:100  Invalid misc:3787   Missed beacon:0

heme@heme-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
heme@heme-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:e1:ac:a7
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e1:22:2d:64
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,06/21/2007,5.3.0.56 ip=192.168.0.139 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
heme@heme-laptop:~$ sudo ifdown wlan0; sudo ifup wlan0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5566
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1f:e1:22:2d:64
Sending on   LPF/wlan0/00:1f:e1:22:2d:64
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1f:e1:22:2d:64
Sending on   LPF/wlan0/00:1f:e1:22:2d:64
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.0.139 from 192.168.0.1
DHCPREQUEST of 192.168.0.139 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.139 from 192.168.0.1
bound to 192.168.0.139 -- renewal in 592789 seconds.



---

### Post by nixscripter on 2009-01-24
It looks like it's connected at the link level. The thing that jumps out at me is you don't have a default route.

Try this: ```
sudo route add default gw **router.ip.address.here**
```

And then try to ping something. If it doesn't work, type the same thing, but "del" instead of "add" to undo it.

---

### Post by Heme on 2009-01-25
Woohoo, works now

The route adding was the trick. Thank you.

---


Edit: Well that was short-lasted

Installed some updates and booted, now it wont work again. Cannot ping the router and tried to del/readd that default route but no progress.

Another edit:

Seems to be on off with working. Works now after new boot..

---

### Post by nixscripter on 2009-01-25
What may be necessary is to add something to your **/etc/network/interfaces** file.

You should see something like:

```

auto wlan0
iface wlan0 inet dhcp

```

Add this below the iface part:

```

# Added by the Ubuntu Forums
    up route add default gw **gateway.ip.address.here**
    down route del default gw **gateway.ip.address.here**
# End Addition

```

See if that makes it work across reboots.

---

### Post by Heme on 2009-01-26
No, it didnt help.

Cant get it to work again, the boot somehow messes up the settings and even tho I drove in all the commands I did before I couldnt make it to work again. After 6 attempts and boots I gave up and switched to windows. 

Cant see what's wrong with it, it has default route, it gets external IP from the router so I dont see how it cant connect the router then..

---

### Post by nixscripter on 2009-01-26
Alright, minor regression then.

Boot cleanly (i.e. without my script, put /etc/network/interfaces back), and then show the routing info, ifconfig for the card, and try scanning: ```
sudo iwlist wlan0 scan
```.

I just want to make sure that your wireless drivers didn't get messed up or something.

---

### Post by Heme on 2009-01-26
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0

eth0      Link encap:Ethernet  HWaddr 00:1b:38:e1:ac:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13548 (13.2 KB)  TX bytes:13548 (13.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:22:2d:64  
          inet addr:192.168.0.139  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e1ff:fe22:2d64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7124 (6.9 KB)  TX bytes:7115 (6.9 KB)
          Interrupt:19 Memory:d0400000-d0410000

heme@heme-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:17:9A:65:E3:7B
                    ESSID:"relacom"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


Clean boot, as requested.

---

### Post by nixscripter on 2009-01-26
Okay, just making sure you're still connected. Like before, it still looks like a routing problem.

More research reveals it was a mistake on my part. Instead of the up and down lines, try adding this to interfaces file: ```
gateway **gw.ip.addr.here**
```

I'm not sure if it will work, but it's the other way to write the same thing.

Try adding it to the file, bringing it up and down, and then if it still doesn't work, run ```
route
``` just to make sure nothing has changed.

---

### Post by Heme on 2009-01-27
No workies

> Route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0

> Route -n:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0

Not sure which you wanted

---

### Post by nixscripter on 2009-01-28
Both tell me what you did: the entry isn't there.

What I'm trying to do, I should explain, is tell your computer to route packets it doesn't know what to do with (i.e. everything outside its local network) to the gateway (your router), beacuse it will pass them on. I'm just having trouble with the syntax of the **/etc/network/interfaces** configuration file.

One more try (crosses fingers):

```

#begin addition
    post-up route add default gw gateway.ip.address.here
    pre-down route del default gw gateway.ip.address.here
#end addition

```

---

### Post by Heme on 2009-01-28
No dice once more

But it seems there are some double entries now:

> heme@heme-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0
heme@heme-laptop:~$ 

Also I took the interfaces file if you spot some anomalies there:

> iface wlan0 inet dhcp
#begin addition
    post-up route add default gw 192.168.0.1
    pre-down route del default gw 192.168.0.1
#end addition
wireless-key {censored}
wireless-essid relacom

auto wlan0

---

### Post by nixscripter on 2009-01-28
Hmm, maybe it was sticking with 0.0.0.0 and I didn't recognize that.

Try one of these: ```
sudo route del default gw 192.168.0.1
```

So there is only one entry. Then it should work.

The only thing that bugs me is that normally DHCP servers send this information to their clients automatically (i.e. what the default gateway is, and what to do with unknown packets). Something must be different about the way DHCP is set up.

---

### Post by Heme on 2009-01-28
Naw, it didnt help..

And after a boot there was double entry again :>

It didnt work at other apartment with another router either tho, so I doubt it's cuz of that. This is getting annoying as well, customized that linux as perfectness but cant get the most vital area to work :L

---

### Post by alwayshear on 2009-01-28
Heme,

I too am new at Linux tinkering but don't give up.  I sense your frustration but consider the gratification when you do finally get it together.  Take a break and come back later with fresh eyes.  I'm anxiously waiting to see your progression through this minor problem.

Good luck,

Mo'

---

### Post by Heme on 2009-01-28
Thanks :>

Yea it's frustrating especially as I dont know anything bout the mechanics linux works on.. but what I've now used it I definitely wanna get it to work perfectly seeing its superiority over windows.

No pain no gain :p

---

### Post by nixscripter on 2009-01-28
Alright, let me try a different tack on this.

Revert the /etc/network/interfaces file back to the way it was, and now look at **/etc/dhcp3/dhclient.conf**, there should be a whole bunch of stuff in the file, but in particular, look at a non-hashed line which looks something like this:

```

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;

```

At the bottom add a specific line like this to tell it to use the same router, no matter what the DHCP server says:

```
supersede routers 192.168.0.1;
```

Then reboot one more time, and hopefully, it will work. If it doesn't, try putting double quotes around the IP address.

---

### Post by Heme on 2009-01-29
Nop, nothing.

Also there wasnt much stuff in that file, only 
> request subnet-mask, broadcast-address, time-offset, routers, domain-name,    domain-name-servers, host-name, ntp-servers;

> PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.139 icmp_seq=1 Destination Host Unreachable


Is there some program that would try autoconffing these, I've heard of some wicd but of course cannot try it w/o internet to connect to repositories.

---

### Post by nixscripter on 2009-01-29
I've never used it, but it's worth a try.

The instructions to install via repository I find are somewhat complicated. An alternative would be to compile it yourself. You can find the source tarball here: [https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)

---

### Post by Heme on 2009-01-29
Hmm, I booted into linux to start installing that proggy.. guess what, net works again.

I tried earlier today, couple clean boots, made some tunings, booted and nothing, now I boot randomly and it works. Cant see logic here :P

Anyway, it seems my old modification of making it use fixed IP instead of dhcp seems to be in use and working atm.

> heme@heme-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0
heme@heme-laptop:~$ 


It seems the same as it used to be. 

If you'd bother to request some commands that list the vital stuff now while it works to see what's changed and narrow the problem down?

Am pretty sure that if I boot I lose net again :>

---

### Post by nixscripter on 2009-01-29
Well, now that it's working, let me see if I can mess it up. ;-)

If you can live with a **fixed** IP, then you can tell the interfaces file to make it work. Something like this should do it:

```

iface wlan0 inet **static**
wireless-key **whatever**
wireless-essid relacom
address **192.168.0.100**
netmask 255.255.255.0
gateway 192.168.0.1

auto wlan0

```

See if that works.

---

### Post by Heme on 2009-01-29
And it stopped working again :>

Booting is a killer. I tried adding that line but of no avail. And dhcp works in windows so I doubt it's even fixed IP.  It just works randomly, there's no sense in it.

Tho I edited that bolded IP with the LAN IP (dont ask why), that's the same what I put to confs when I first time put it to static.

---

### Post by nixscripter on 2009-01-29
In that case, I don't know what I can say, except to remember that trick when it doesn't work. Manually type: ```
sudo route add default gw 192.168.0.1
```

If it worked before, it should work again.

---

### Post by Heme on 2009-01-30
Rejoice!

I got it working. 

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

^ was the trick

Had to install madwifi and enable some ath_pci stuff but now it works. Ahh, the satisfaction ;)

---

### Post by nixscripter on 2009-01-30
Great. Please mark the thread as solved (under the Thread tools menu, I think).

---

