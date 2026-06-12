---
title: "Installing new wireless pci card after installation?"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by daller on 2007-01-19
Hi There,

Just bought myself a wireless card with the Atheros AR2413A chipset.

lspci finds it:

```
varkstedet@varkstedet-desktop:~$ lspci | grep "Wireless"
00:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
```

But it's not listed as eth1, or anything else...

```
varkstedet@varkstedet-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:DC:EE:3E:AA
          inet addr:192.168.0.109  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:dcff:feee:3eaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1051 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:710431 (693.7 KiB)  TX bytes:153950 (150.3 KiB)
          Interrupt:217 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

It's installed after linux-installation, so is there anything I should do in order to make it work?

---

### Post by lukew on 2007-01-19
You card looks like it is recognized as a device but does not have a valid drivers. 

Check your card in 

[HTML]https://help.ubuntu.com/community/WifiDocs[/HTML]

and follow the instructions for your card. If any extra files/firmware/drivers are required they will give yo the link to a version which is known to work.

Luke

---

