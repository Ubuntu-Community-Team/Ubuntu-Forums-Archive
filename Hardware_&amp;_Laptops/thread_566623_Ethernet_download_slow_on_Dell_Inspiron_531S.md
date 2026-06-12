---
title: "Ethernet download slow on Dell Inspiron 531S"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by sbaker3 on 2007-10-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/148738](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/148738) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Network download is very slow for me on my machine running generic gutsy on AMD Athlon(tm) 64 X2 Dual Core with forcedeth network driver.

Here is a typical iperf run:
```

$ iperf -c 192.168.1.50 -d
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.1.50, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[ 5] local 192.168.1.101 port 37835 connected with 192.168.1.50 port 5001
[ 4] local 192.168.1.101 port 5001 connected with 192.168.1.50 port 56946
[ 5] 0.0-10.0 sec 48.4 MBytes 40.6 Mbits/sec
[ 4] 0.0-10.2 sec 1.57 MBytes 1.29 Mbits/sec
```

Ifconfig shows RX packet errors:
```
$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1A:A0:53:4D:FB
          inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:73886 errors:3443 dropped:0 overruns:0 frame:3391
          TX packets:108585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27746730 (26.4 MB) TX bytes:140126662 (133.6 MB)
          Interrupt:16 Base address:0x4000
```

Pertinent excerpts from lshw:
```
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1a:a0:53:4d:fb
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.1.101 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
```

```

$ uname -a
Linux steveb-desktop 2.6.22-12-generic #1 SMP Sun Sep 23 18:11:30 GMT 2007 i686 GNU/Linux

```
In addition to the default boot options following boot options were tried which had no effect on iperf stats speed:
```

noapictimer irqpoll
noapic nolapic
noapic acpi=noirq
noapic acpi=off
noapictimer
noapic acpi=noirq nolapic

```
The following boot options segfaulted on boot:
```

clock=pmtmr notsc
notsc
```

Disabling fglrx had no effect on iperf stats.

The slow download has occured attached to 2 different routers and different cables.

See the attached launchpad bug for log file attachments

cheers

---

### Post by sbaker3 on 2007-10-04
ping

---

