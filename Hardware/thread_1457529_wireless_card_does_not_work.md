---
title: "wireless card does not work"
date: 2010-04-18
forum: Hardware
---

### Post by gtarabat on 2010-04-18
Hello everybody.

I 've been trying to install a TP-LINK TL-WN951N card on a desktop pc.
The current driver (ath9k) seems not to be working. It is running Karmic Koala
with 2.6.31-20-generic kernel.
I tried to use the windows drivers with ndiswrapper but the problem remains.
Here are some info from the system

**lspci**
```

...
02:02.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:0d.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

```**lspci -n**
```

...
02:0d.0 0280: 168c:0023 (rev 01)

```**iwconfig**
```

lo        no wireless extensions.

eth1      no wireless extensions.

```**ifconfig**
```

eth1      Link encap:Ethernet  HWaddr 00:08:a1:aa:7e:dc  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:feaa:7edc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4905361 (4.9 MB)  TX bytes:606913 (606.9 KB)
          Interrupt:18 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:340 (340.0 B)  TX bytes:340 (340.0 B)

```**dmesg**
```

...
[   15.174473] ath9k 0000:02:0d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.285369] ath9k: timeout (100000 us) on reg 0x7044: 0xbadc4ffe & 0x0000000f != 0x00000002
[   15.285378] ath9k: Couldn't reset chip
[   15.285391] ath9k: Unable to attach hardware; HAL status -5
...
[   15.746325] ath9k 0000:02:0d.0: PCI INT A disabled
...

```Thanks a lot.

---

