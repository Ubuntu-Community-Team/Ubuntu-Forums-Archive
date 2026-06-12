---
title: "Dell Inspiron N4030, Networking issues"
date: 2011-02-10
forum: Hardware
---

### Post by Tensk8 on 2011-02-10
Hi experts,

I have an Dell Inspiron N4030 with ubuntu 10.10. 

When I power up the computer the wired NIC start fine and it request the IP and I even can access the Internet.  Ten of five minutes later the NIC stop working. 

This issue happened in the same way if I unplug the cable and plug it again, the networking stop.


The fast ethernet is an Atheros Communication AR8152v2.0

Any help will be appreciated

---

### Post by Tensk8 on 2011-02-14
This is the log

Feb 14 08:57:13 Andre-Dell NetworkManager[992]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Feb 14 08:57:13 Andre-Dell kernel: [ 1552.185906] atl1c 0000:13:00.0: atl1c: eth0 NIC Link is Down
Feb 14 08:57:14 Andre-Dell kernel: [ 1553.839490] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Feb 14 08:57:17 Andre-Dell NetworkManager[992]: <info> (eth0): device state change: 8 -> 2 (reason 40)
Feb 14 08:57:17 Andre-Dell NetworkManager[992]: <info> (eth0): deactivating device (reason: 40).
Feb 14 08:57:17 Andre-Dell NetworkManager[992]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1349
Feb 14 08:57:17 Andre-Dell avahi-daemon[991]: Withdrawing address record for 192.168.60.31 on eth0.
Feb 14 08:57:17 Andre-Dell avahi-daemon[991]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.60.31.
Feb 14 08:57:17 Andre-Dell avahi-daemon[991]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb 14 08:57:17 Andre-Dell NetworkManager[992]: <info> Policy set 'Auto guest' (eth1) as default for IPv4 routing and DNS.
Feb 14 08:57:17 Andre-Dell NetworkManager[992]: <info> Updating /etc/hosts with new system hostname
Feb 14 08:57:17 Andre-Dell NetworkManager[992]: <info> Policy set 'Auto guest' (eth1) as default for IPv4 routing and DNS.
Feb 14 08:57:17 Andre-Dell nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Feb 14 08:57:17 Andre-Dell nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Feb 14 08:57:24 Andre-Dell kernel: [ 1563.952076] atl1c 0000:13:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> (eth0): carrier now ON (device state 2)
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) starting connection 'Auto eth0'
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> dhclient started with pid 2163
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 14 08:57:24 Andre-Dell dhclient: Internet Systems Consortium DHCP Client V3.1.3
Feb 14 08:57:24 Andre-Dell dhclient: Copyright 2004-2009 Internet Systems Consortium.
Feb 14 08:57:24 Andre-Dell dhclient: All rights reserved.
Feb 14 08:57:24 Andre-Dell dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Feb 14 08:57:24 Andre-Dell dhclient:
Feb 14 08:57:24 Andre-Dell NetworkManager[992]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Feb 14 08:57:24 Andre-Dell dhclient: Listening on LPF/eth0/f0:4d:a2:a0:5f:60
Feb 14 08:57:24 Andre-Dell dhclient: Sending on   LPF/eth0/f0:4d:a2:a0:5f:60
Feb 14 08:57:24 Andre-Dell dhclient: Sending on   Socket/fallback
Feb 14 08:57:24 Andre-Dell dhclient: DHCPREQUEST of 192.168.60.31 on eth0 to 255.255.255.255 port 67
Feb 14 08:57:27 Andre-Dell dhclient: DHCPREQUEST of 192.168.60.31 on eth0 to 255.255.255.255 port 67
Feb 14 08:57:27 Andre-Dell dhclient: DHCPACK of 192.168.60.31 from 192.168.60.5
Feb 14 08:57:27 Andre-Dell dhclient: bound to 192.168.60.31 -- renewal in 340883 seconds.
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info>   address 192.168.60.31
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info>   prefix 24 (255.255.255.0)
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info>   gateway 192.168.60.254
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info>   nameserver '196.40.3.8'
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info>   nameserver '4.2.2.2'
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info>   nameserver '8.8.8.8'
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info>   nameserver '196.40.3.9'
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info>   domain name 'spcinternacional.com'
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Feb 14 08:57:27 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Feb 14 08:57:27 Andre-Dell avahi-daemon[991]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.60.31.
Feb 14 08:57:27 Andre-Dell avahi-daemon[991]: New relevant interface eth0.IPv4 for mDNS.
Feb 14 08:57:27 Andre-Dell avahi-daemon[991]: Registering new address record for 192.168.60.31 on eth0.IPv4.
Feb 14 08:57:28 Andre-Dell NetworkManager[992]: <info> Policy set 'Auto guest' (eth1) as default for IPv4 routing and DNS.
Feb 14 08:57:28 Andre-Dell NetworkManager[992]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Feb 14 08:57:28 Andre-Dell NetworkManager[992]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Feb 14 08:57:28 Andre-Dell NetworkManager[992]: <info> Updating /etc/hosts with new system hostname
Feb 14 08:57:28 Andre-Dell NetworkManager[992]: <info> Activation (eth0) successful, device activated.
Feb 14 08:57:28 Andre-Dell NetworkManager[992]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Feb 14 08:57:28 Andre-Dell nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Feb 14 08:57:28 Andre-Dell nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.

---

