---
title: "VirtualBox Networking not working"
date: 2008-08-12
forum: General Help
---

### Post by supradave on 2008-08-12
I have set up multiple FC6 VirtualBoxes for testing on my Ubuntu desktop machine. I have them bumped down to 64MB RAM because they're not gui-based boxes. For Wed-Fri of last week, I had them all working over the bridged network that I have created. When I tried to start them back up on Monday, I wasn't able to attach to the network. The NAT network worked, but I need to have the bridged addresses to do the testing that I need to do. I have tried recreating the br0 interface. I just don't know what else to try.

Here is the ifconfig br0:
br0 Link encap:Ethernet HWaddr 00:1a:4d:46:fc:78
inet addr:192.168.250.42 Bcast:192.168.250.255 Mask:255.255.255.0
inet6 addr: fe80::21a:4dff:fe46:fc78/64 Scope:Link
UP BROADCAST RUNNING PROMISC MULTICAST MTU:1500 Metric:1
RX packets:7819141 errors:0 dropped:0 overruns:0 frame:0
TX packets:4012802 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2461653577 (2.2 GB) TX bytes:294316920 (280.6 MB)

eth1 Link encap:Ethernet HWaddr 00:1a:4d:46:fc:78
inet6 addr: fe80::21a:4dff:fe46:fc78/64 Scope:Link
UP BROADCAST RUNNING PROMISC MULTICAST MTU:1500 Metric:1
RX packets:7820485 errors:0 dropped:0 overruns:0 frame:0
TX packets:4013721 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2571293757 (2.3 GB) TX bytes:294508078 (280.8 MB)
Interrupt:219 Base address:0xc000

And the vb interface:
root Link encap:Ethernet HWaddr 00:ff:44:ab:7e:21
inet6 addr: fe80::2ff:44ff:feab:7e21/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:566 errors:0 dropped:0 overruns:0 frame:0
TX packets:164 errors:0 dropped:412 overruns:0 carrier:0
collisions:0 txqueuelen:500
RX bytes:120025 (117.2 KB) TX bytes:18642 (18.2 KB)

Here is my /etc/vbox/interfaces:
cat /etc/vbox/interfaces
# This file is for registering VirtualBox permanent host networking interfaces
# and optionally adding them to network bridges on the host.
# Each line should be of the format <interface name> <user name> [<bridge>].

client dave br0
dns dave br0
attacker dave br0
root dave br0
tld dave br0
windows dave br0
hardy dave br0
nsdmaster dave br0
bindslave dave br0

I have even set NAT through iptables.

Thanks,
Dave

---

### Post by supradave on 2008-08-12
It appears there's some problem with the /etc/vbox/interfaces getting read appropriately. Therefore, you simply have to just rerun:
sudo VBoxAddIF interfacename interface

e.g. sudo VBoxAddIF client br0

---

