---
title: "How do I use DHCP ?"
date: 2005-11-15
forum: General Help
---

### Post by pbb on 2005-11-15
Another newbie-question!

I'm trying to setup Ubuntu so that it can share it's internet connection with another WinXP machine.

So far I've managed to get IP-based traffic going (that is, on the XP machine I can reach websites by their IP address), but I would like to enable automatic IP and DNS assignment to the XP machine.

Am I right this means running a DHCP server on Ubuntu? And how do I run this? I've tried installing "dhcp3-server" using the Package Manager, but after the installation it says "* Starting DHCP server... [fail]".

Thanks, Peter

---

### Post by grendel_khan on 2005-11-15
Is there anything in the syslogs about why it might have failed? Can you try manually running the daemon from a shell and seeing if it spits an error message at you? Did you change the config file before starting it? It might be choking on a bad configuration; the syslog might tell you more.

---

### Post by Sheco on 2005-11-15
You have to edit /etc/dhcp3/dhcpd.conf first and it has to have something like this:

subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.1 192.168.2.253;
  option routers 192.168.2.254;
}

---

### Post by pbb on 2005-11-15
Grendel, thanks for the reply.

I really a newbie -- can you tell me where to find the syslog ??

I tried to manually run the deamon with the command "/etc/init.d/dhcp3-server start", but that gave the same error.

I did not make any modifications to the config file. (Wouldn't even know where to find that.)

---

### Post by pbb on 2005-11-15
Sheco, I assigned 192.168.0.1 to my card, should my config be as follows?

```
subnet 192.168.0.1 netmask 255.255.255.0 {
range 192.168.0.2 192.168.0.253;
option routers 192.168.0.254;
}
```

---

### Post by kosmic on 2005-11-15
Yes it is ok, your XP box should assing a Ip automaticaly inside the mask 192.168.0.*

---

### Post by Bachstelze on 2005-11-15
For me it worked fine without having to edit anything. I set a static IP for my XP machine (192.168.0.1) and let Ubuntu with DHCP, plug in, activate the eth0 interface in Ubuntu, voil&#224; :D

---

### Post by pbb on 2005-11-15
[QUOTE=HymnToLife]I set a static IP for my XP machine (192.168.0.1)[/QUOTE]

Yeah, but my problem is that if I set a static IP address to XP, I also have to set a static DNS server. I prefer to have XP figure that out by itself...

---

### Post by grendel_khan on 2005-11-16
[QUOTE=pbb]Grendel, thanks for the reply.

I really a newbie -- can you tell me where to find the syslog ??

I tried to manually run the deamon with the command "/etc/init.d/dhcp3-server start", but that gave the same error.

I did not make any modifications to the config file. (Wouldn't even know where to find that.)[/QUOTE]

My bad; the syslog is in /var/log. It's most likely there as /var/log/syslog.0. Doing a ```
$ tail -f /var/log/syslog.0
``` in one terminal window will let you see the syslog messages as they're generated while you do that sudo /etc/init.d/dhcp3-server start you were doing.

To start the server manually (that is, without using the init.d script), you can try ```
$ sudo /usr/sbin/dhcpd3
``` and see what the output is.

Do you get anything on the syslog? Anything more helpful with this?

---

### Post by pbb on 2005-11-20
With Sheco's help, I managed to get DHCP running now. The contents of my  /etc/dhcp3/dhcpd.conf is as follows:

```
subnet 192.168.0.0 netmask 255.255.255.0 {
 range 192.168.0.1 192.168.0.255;
 option routers 192.168.0.1;
 option domain-name-servers 192.168.0.1;
}
```

The second computer on the network now gets an IP address assigned (192.168.0.255), but has no internet trafic at all now!

Following is the part from /var/log/syslog (not syslog.0, is that a problem?) that I think is important here (sorry for the extensive code, I do not know which parts are important and which not):

```
Nov 20 14:54:00 localhost dhcpd: Internet Systems Consortium DHCP Server V3.0.2
Nov 20 14:54:00 localhost dhcpd: Copyright 2004 Internet Systems Consortium.
Nov 20 14:54:00 localhost dhcpd: All rights reserved.
Nov 20 14:54:00 localhost dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Nov 20 14:54:00 localhost dhcpd: Wrote 255 leases to leases file.
Nov 20 14:54:00 localhost dhcpd: 
Nov 20 14:54:00 localhost dhcpd: No subnet declaration for eth0 (10.0.0.4).
Nov 20 14:54:00 localhost dhcpd: ** Ignoring requests on eth0.  If this is not what
Nov 20 14:54:00 localhost dhcpd:    you want, please write a subnet declaration
Nov 20 14:54:00 localhost dhcpd:    in your dhcpd.conf file for the network segment
Nov 20 14:54:00 localhost dhcpd:    to which interface eth0 is attached. **
Nov 20 14:54:00 localhost dhcpd: 
Nov 20 14:54:32 localhost dhcpd: DHCPDISCOVER from <MAC removed> via eth1
Nov 20 14:54:32 localhost dhcpd: icmp_echorequest 192.168.0.255: Permission denied
Nov 20 14:54:33 localhost dhcpd: DHCPOFFER on 192.168.0.255 to <MAC removed> (<PC 2>) via eth1
Nov 20 14:54:33 localhost dhcpd: DHCPREQUEST for 192.168.0.255 (192.168.0.1) from <MAC removed> (<PC 2>) via eth1
Nov 20 14:54:33 localhost dhcpd: DHCPACK on 192.168.0.255 to <MAC removed> (<PC 2>) via eth1
Nov 20 14:54:35 localhost dhcpd: DHCPINFORM from 192.168.0.255 via eth1: not authoritative for subnet 192.168.0.0
Nov 20 14:54:35 localhost dhcpd: If this DHCP server is authoritative for that subnet,
Nov 20 14:54:35 localhost dhcpd: please write an `authoritative;' directive either in the
Nov 20 14:54:35 localhost dhcpd: subnet declaration or in some scope that encloses the
Nov 20 14:54:35 localhost dhcpd: subnet declaration - for example, write it at the top
Nov 20 14:54:35 localhost dhcpd: of the dhcpd.conf file.
Nov 20 14:54:38 localhost dhcpd: DHCPINFORM from 192.168.0.255 via eth1: not authoritative for subnet 192.168.0.0
Nov 20 14:56:28 localhost kernel: [4295808.748000] eth1: network connection down
Nov 20 14:56:30 localhost kernel: [4295810.335000] eth1: network connection up using port A
Nov 20 14:56:30 localhost kernel: [4295810.335000]     speed:           100
Nov 20 14:56:30 localhost kernel: [4295810.335000]     autonegotiation: yes
Nov 20 14:56:30 localhost kernel: [4295810.335000]     duplex mode:     full
Nov 20 14:56:30 localhost kernel: [4295810.335000]     flowctrl:        none
Nov 20 14:56:30 localhost kernel: [4295810.335000]     irq moderation:  disabled
Nov 20 14:56:30 localhost kernel: [4295810.335000]     tcp offload:     enabled
Nov 20 14:56:30 localhost kernel: [4295810.335000]     scatter-gather:  enabled
Nov 20 14:56:30 localhost kernel: [4295810.335000]     tx-checksum:     enabled
Nov 20 14:56:30 localhost kernel: [4295810.335000]     rx-checksum:     enabled
Nov 20 14:56:30 localhost kernel: [4295810.335000]     rx-polling:      enabled
Nov 20 14:57:04 localhost kernel: [4295844.975000] eth1: network connection down
Nov 20 14:57:06 localhost kernel: [4295846.580000] eth1: network connection up using port A
Nov 20 14:57:06 localhost kernel: [4295846.580000]     speed:           100
Nov 20 14:57:06 localhost kernel: [4295846.580000]     autonegotiation: yes
Nov 20 14:57:06 localhost kernel: [4295846.580000]     duplex mode:     full
Nov 20 14:57:06 localhost kernel: [4295846.580000]     flowctrl:        none
Nov 20 14:57:06 localhost kernel: [4295846.580000]     irq moderation:  disabled
Nov 20 14:57:06 localhost kernel: [4295846.580000]     tcp offload:     enabled
Nov 20 14:57:06 localhost kernel: [4295846.580000]     scatter-gather:  enabled
Nov 20 14:57:06 localhost kernel: [4295846.580000]     tx-checksum:     enabled
Nov 20 14:57:06 localhost kernel: [4295846.580000]     rx-checksum:     enabled
Nov 20 14:57:06 localhost kernel: [4295846.580000]     rx-polling:      enabled
Nov 20 14:57:14 localhost dhcpd: DHCPREQUEST for 192.168.0.255 from <MAC removed> (<PC 2>) via eth1
Nov 20 14:57:14 localhost dhcpd: DHCPACK on 192.168.0.255 to <MAC removed> (<PC 2>) via eth1
Nov 20 14:57:55 localhost dhcpd: DHCPINFORM from 192.168.0.255 via eth1: not authoritative for subnet 192.168.0.0
Nov 20 14:57:58 localhost dhcpd: DHCPINFORM from 192.168.0.255 via eth1: not authoritative for subnet 192.168.0.0
Nov 20 15:03:53 localhost dhcpd: DHCPINFORM from 192.168.0.255 via eth1: not authoritative for subnet 192.168.0.0
Nov 20 15:03:56 localhost dhcpd: DHCPINFORM from 192.168.0.255 via eth1: not authoritative for subnet 192.168.0.0
Nov 20 15:05:22 localhost last message repeated 2 times
Nov 20 15:05:59 localhost kernel: [4296379.582000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Nov 20 15:05:59 localhost kernel: [4296379.582000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Nov 20 15:05:59 localhost kernel: [4296379.730000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Nov 20 15:05:59 localhost kernel: [4296379.730000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Nov 20 15:06:03 localhost dhcpd: DHCPREQUEST for 192.168.0.255 from <MAC removed> (<PC 2>) via eth1
Nov 20 15:06:03 localhost dhcpd: DHCPACK on 192.168.0.255 to <MAC removed> (<PC 2>) via eth1
Nov 20 15:06:03 localhost dhcpd: send_packet: Permission denied
Nov 20 15:06:11 localhost dhcpd: DHCPREQUEST for 192.168.0.255 from <MAC removed> (<PC 2>) via eth1
Nov 20 15:06:11 localhost dhcpd: DHCPACK on 192.168.0.255 to <MAC removed> (<PC 2>) via eth1
Nov 20 15:06:11 localhost dhcpd: send_packet: Permission denied
Nov 20 15:06:46 localhost dhcpd: DHCPINFORM from 192.168.0.255 via eth1: not authoritative for subnet 192.168.0.0
Nov 20 15:06:50 localhost dhcpd: DHCPINFORM from 192.168.0.255 via eth1: not authoritative for subnet 192.168.0.0
Nov 20 15:06:58 localhost dhcpd: DHCPREQUEST for 192.168.0.255 from <MAC removed> (<PC 2>) via eth1
Nov 20 15:06:58 localhost dhcpd: DHCPACK on 192.168.0.255 to <MAC removed> (<PC 2>) via eth1
Nov 20 15:06:58 localhost dhcpd: send_packet: Permission denied
Nov 20 15:07:01 localhost dhcpd: DHCPREQUEST for 192.168.0.255 from <MAC removed> (<PC 2>) via eth1
Nov 20 15:07:01 localhost dhcpd: DHCPACK on 192.168.0.255 to <MAC removed> (<PC 2>) via eth1
Nov 20 15:07:01 localhost dhcpd: send_packet: Permission denied
Nov 20 15:07:10 localhost dhcpd: DHCPREQUEST for 192.168.0.255 from <MAC removed> (<PC 2>) via eth1
Nov 20 15:07:10 localhost dhcpd: DHCPACK on 192.168.0.255 to <MAC removed> (<PC 2>) via eth1
Nov 20 15:07:10 localhost dhcpd: send_packet: Permission denied
Nov 20 15:07:15 localhost dhcpd: DHCPDISCOVER from <MAC removed> (<PC 2>) via eth1
Nov 20 15:07:15 localhost dhcpd: DHCPOFFER on 192.168.0.255 to <MAC removed> (<PC 2>) via eth1
Nov 20 15:07:15 localhost dhcpd: DHCPREQUEST for 192.168.0.255 (192.168.0.1) from <MAC removed> (<PC 2>) via eth1
Nov 20 15:07:15 localhost dhcpd: DHCPACK on 192.168.0.255 to <MAC removed> (<PC 2>) via eth1
Nov 20 15:07:31 localhost dhcpd: DHCPINFORM from 192.168.0.255 via eth1: not authoritative for subnet 192.168.0.0
Nov 20 15:07:34 localhost dhcpd: DHCPINFORM from 192.168.0.255 via eth1: not authoritative for subnet 192.168.0.0
```

Does anybody know what I am doing wrong? I don't really understand the error messages in this code...

---

### Post by i-Buntu-2 on 2007-12-18
Hi,

Try editing your range:

range 192.168.0.1 192.168.0.255;

change this to:

range 192.168.0.1 192.168.0.254;

192.168.0.255 is the scopes broadcast address and should not be part of the dhcp pool

Let me know how you get on

---

### Post by grendel_khan on 2007-12-18
> **i-Buntu-2 said:**
> Hi,

Try editing your range:

range 192.168.0.1 192.168.0.255;

change this to:

range 192.168.0.1 192.168.0.254;

192.168.0.255 is the scopes broadcast address and should not be part of the dhcp pool

Let me know how you get on
That's a really good point, and there's a small hand-shaped imprint on my forehead because I didn't notice it. Given that we're not trying to squeeze every drop of available address space out of the subnet, we might as well exclude the server's IP as well. Heck, the default configuration for most DHCP-supporting routers runs as the following:

range 192.168.0.100 192.168.0.254;

You're probably not going to put a hundred and fifty-five machines on a home network anyway--this range should work fine.

---

