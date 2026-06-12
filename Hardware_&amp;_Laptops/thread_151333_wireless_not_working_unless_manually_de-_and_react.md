---
title: "wireless not working unless manually de- and reactivated"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by rotanil on 2006-03-27
My wireless connection doesn't give me internet access, unless I start network-admin, de-activate the wireless connection (ifdown eth0), activate it again (ifup eth0) and then press OK (dhclient eth0).

---

### Post by Titus A Duxass on 2006-03-28
Give us some more information please.

Card type, breezy or dapper, etc.

Sounds like you need to modify your /etc/network/inferfaces file.

Are you using ndiswrapper?

Things like this are helpful.

---

### Post by rotanil on 2006-03-28
Card is a RT2500, I'm using Breezy and ndiswrapper isn't installed. I am already aware of /etc/network/interfaces, but haven't any success messing with it.

---

### Post by Titus A Duxass on 2006-03-28
What do you mean you have not had any success messing with it?

What does it look like now?

Do you have a line "auto wlan0"?

---

### Post by rotanil on 2006-03-28
The device is called eth0, and there is an "auto eth0" in /etc/network/interfaces. Remember that eth0 is considered to be active by network-admin at the start, and needs to be deactivated first.
Content of /etc/network/interfaces is (without comments):
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp
wireless-essid my_essid
wireless-key s:my_key

auto eth0

```

---

### Post by rotanil on 2006-03-29
At the risk of making a faux pas here, I'm bumping this thread with this post.

---

### Post by jamesr on 2006-03-29
I know that you can activate manually, but can you post the output of ```
sudo ifconfig -a
sudo iwconfig -a
```

show the output of```
sudo dhclient eth0
```

---

### Post by swinster on 2006-03-30
jamesr - I need also to get some info like this for a similar issue. Why to I send the output of the command such as ifconfig and iwconfig (or anything for that mater) to a text file?

---

### Post by jamesr on 2006-03-30
You should be able to do ```
sudo ifconfig -a > file1
``` and that will generate a file1 containing the output but of course file1 is overwritten every time and no warning posted.

---

### Post by rotanil on 2006-03-30
[QUOTE=jamesr]I know that you can activate manually, but can you post the output of ```
sudo ifconfig -a
```[/QUOTE]
```

eth0      Link encap:Ethernet  HWaddr 00:50:18:44:91:3F
          inet6 addr: fe80::250:18ff:fe44:913f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:146480 (143.0 KiB)
          Interrupt:11 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
> 
```

sudo iwconfig -a
```

```

-a        No such device

```
> show the output of```
sudo dhclient eth0
```
```

Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:50:18:44:91:3f
Sending on   LPF/eth0/00:50:18:44:91:3f
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
Trying recorded lease 192.168.1.7
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```
This is all before I get the connection to work.

---

### Post by rotanil on 2006-04-01
Bump

---

### Post by jamesr on 2006-04-01
Sorry about the delay but I had medical matters to solve.

The sudo dhclient eth0 output is indicating that is not getting a lease and reverting to an address 192.168.1.7 but thaen cannoit ping the router @192.168.1.1 which I am assuming is the router address

```
dmesg | grep eth0
```

---

### Post by rotanil on 2006-04-01
[QUOTE=jamesr]Sorry about the delay but I had medical matters to solve.

The sudo dhclient eth0 output is indicating that is not getting a lease and reverting to an address 192.168.1.7 but thaen cannoit ping the router @192.168.1.1 which I am assuming is the router address

```
dmesg | grep eth0
```[/QUOTE]
First I get nothing. After a while however I get:
```

[4294802.636000] eth0: no IPv6 routers present

```
When it's working again, I get:
```

[4294802.636000] eth0: no IPv6 routers present
[4296434.724000] eth0: no IPv6 routers present

```

---

### Post by jamesr on 2006-04-01
1)  it may a good idea to deactivate ipv6
2) the bootup process seems not to be finding the NIC as eth0

```
sudo miitools
sudo lspci
```

---

### Post by rotanil on 2006-04-02
[QUOTE=jamesr]1)  it may a good idea to deactivate ipv6[/QUOTE]
I don't know how to do that.
> 
2) the bootup process seems not to be finding the NIC as eth0

```
sudo miitools
```
I assume you mean "sudo mii-tool" instead. Output is:
```

SIOCGMIIPHY on 'eth0' failed: Operation not supported
no MII interfaces found

```
> ```

sudo lspci
```
Relevant line is:
```

0000:00:09.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

```

---

### Post by jamesr on 2006-04-02
Sorry about the mistyping about the mii-tool command.
Can you check if it coming up as ra0```
dmesg | grep ra0
lsmod
```

---

### Post by lit0 on 2006-04-03
I create a little script that work to me.

I always when start my ubuntu, I was without wireless. First open wavemon to test the network, then open the network-admin and activate and deactivate the wireless card and then I was connected.

I create a bash script:

```

#! /bin/sh

conectado=`ifconfig | grep ath0`

if [ "$conectado" == "" ]; then
        ifup ath0
fi

exit 0

```

I put it in /etc/init.d/wifi and I make a link to /etc/rc5.d/S19wifi to test the network on ubuntu load.

Also I have installed a cron each 10 minutes to up the network if down:

```

*/10 * * * * /bin/sh /etc/init.d/wifi

```

Now, I always have wireless. :KS :KS

---

### Post by rotanil on 2006-04-03
[QUOTE=jamesr]Sorry about the mistyping about the mii-tool command.
Can you check if it coming up as ra0```
dmesg | grep ra0
```[/QUOTE]
Nothing.
> ```

lsmod
```
Amongst others I see the following line:
```

rt2500                179684  1

```

---

### Post by jamesr on 2006-04-04
I am puzzled, I did some research and all of the cases it seemed to be ra0 and not eth0 in the examples . Obviously it seeing the card as rt2500. If I can find my original references, I will post them.

---

### Post by jamesr on 2006-04-04
Do you per chance have 2 NICs in the system a wireless and wired?

```
sudo modprobe rt2500
sudo ifconfig -a
```

---

### Post by rotanil on 2006-04-04
I *had* 2 NICs in the system at one time, but had to remove the wired one because sound stopped working. Also, if it's any help, the wireless card was actually designated as ra0 for a short while, before it changed to, I believe, eth1.

---

### Post by rotanil on 2006-04-06
Using network-manager doesn't work either.

---

### Post by jamesr on 2006-04-06
Any changeseen after following the response  with the modprobe and the ifconfig. Got to find my notes on disabling ipv6

---

### Post by rotanil on 2006-04-06
[QUOTE=jamesr]Any changeseen after following the response  with the modprobe and the ifconfig.[/QUOTE]
i don't believe so.

---

