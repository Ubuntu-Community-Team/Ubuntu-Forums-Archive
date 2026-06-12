---
title: "problems with tg3 ethernet driver"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by yoginho on 2006-03-31
Hi there,

I've got a Tyan Thunder K8W motherboard with a Broadcom BCM5703C
Gigabit ethernet card. My box is running Kubuntu 5.10 (Breezy Badger)
with the tg3 driver:

# uname -a
Linux <hostname> 2.6.12-10-amd64-generic #1 Sat Mar 11 16:15:30 UTC
2006 x86_64 GNU/Linux
# sudo ethtool -i eth0
driver: tg3
version: 3.31
firmware-version:
bus-info: 0000:02:09.0

Whenever I transfer large amounts of data from my laptop to this
machine via ssh, I get a

'Received disconnect from <hostname>: 2: Corrupted MAC on input.'

usually fairly early during the transfer. I don't think this is a bug
in OpenSSH (I'm using: OpenSSH_4.1p1 Debian-7ubuntu4.1, OpenSSL 0.9.7g
11 Apr 2005).

I've found quite a bit of information on this error online but none of
it is relevant to me, since neither do I have any linksys routers on
the network, nor did switching off checksumming on the interface
('ethtool -K eth0 tx off rx off') do any good.

The problem happens only when I transfer data over the local network,
but not if I transfer data from home (slow, since via cable modem).
This makes me think that the problem has something to do with high
transfer speed.

See below for the precise settings of the NIC. I have tried to lower
the card's speed by using 'sudo ethtool -s eth0 speed 10', but this
does not seem to have any effect. Anyway, permanently lowering the
interface's speed does not seem very appealing to me.

Any suggestions? Is this a known bug in the tg3 driver? I haven't come
across it anywhere. Is it worth trying the outdated bcm5700 driver for
Broadcom 57** cards, instead of tg3?

Thanks for your help.
Yogi

# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:E0:81:34:38:90
          inet addr:131.111.111.245  Bcast:131.111.255.255
Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fe34:3890/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:157340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:78989270 (75.3 MiB)  TX bytes:2088172 (1.9 MiB)
          Interrupt:24

# sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes

---

