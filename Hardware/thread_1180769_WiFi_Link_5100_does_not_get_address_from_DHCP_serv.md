---
title: "WiFi Link 5100 does not get address from DHCP server"
date: 2009-06-07
forum: Hardware
---

### Post by cubeek on 2009-06-07
Hi,

I have a problem with new Kubuntu 9.03 Jaunty. When I wanna connect to network via wifi and WEP security, the DHCP discovery fails. If I turn security off, it connects without problems. I have tried to find similar problem, but I haven't found anything.

Here's the line from lspci
```
14:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
```

I would appreciate any idea or help. Thanks.

---

### Post by aleivag on 2009-08-10
i have the same problem width the same card in ubuntu 9.04 jaunty... when tring to conect to (some, not all weps) it fail to discover a dhcp server, i test the network in other machines width diferent OS and diferent wifi card, and the only combination it fail is ubuntu + wifi link 5100.

the problem is getting the ip.

---

### Post by sergiom99 on 2009-08-10
Network Manager has been reported as "broken" when trying to connecto to encrypted networks.
Try wicd instead, works much better
```
sudo apt-get install wicd
```

Good luck.

---

### Post by aleivag on 2009-08-10
actualy all the test where made with wicd... no luck... the problem is not NetworkManager... is dhclient + the wireless card...

dhclient cant DISCOVER a dhcp host i will post the syslog of wicd alter today (when i get home)

thanx

---

### Post by aleivag on 2009-08-10
the syslog output is:


```

Aug 10 21:31:46 ACERX dhclient: Internet Systems Consortium DHCP Client V3.1.1
Aug 10 21:31:46 ACERX dhclient: Copyright 2004-2008 Internet Systems Consortium.
Aug 10 21:31:46 ACERX dhclient: All rights reserved.
Aug 10 21:31:46 ACERX dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug 10 21:31:46 ACERX dhclient: 
Aug 10 21:31:46 ACERX dhclient: wmaster0: unknown hardware address type 801
Aug 10 21:31:46 ACERX dhclient: wmaster0: unknown hardware address type 801
Aug 10 21:31:46 ACERX dhclient: Bind socket to interface: No such device
Aug 10 21:31:46 ACERX dhclient: Internet Systems Consortium DHCP Client V3.1.1
Aug 10 21:31:46 ACERX dhclient: Copyright 2004-2008 Internet Systems Consortium.
Aug 10 21:31:46 ACERX dhclient: All rights reserved.
Aug 10 21:31:46 ACERX dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug 10 21:31:46 ACERX dhclient: 
Aug 10 21:31:46 ACERX dhclient: wmaster0: unknown hardware address type 801
Aug 10 21:31:46 ACERX dhclient: wmaster0: unknown hardware address type 801
Aug 10 21:31:46 ACERX dhclient: Bind socket to interface: No such device
Aug 10 21:31:46 ACERX kernel: [  504.750694] Registered led device: iwl-phy0:radio
Aug 10 21:31:46 ACERX kernel: [  504.750720] Registered led device: iwl-phy0:assoc
Aug 10 21:31:46 ACERX kernel: [  504.750743] Registered led device: iwl-phy0:RX
Aug 10 21:31:46 ACERX kernel: [  504.750765] Registered led device: iwl-phy0:TX
Aug 10 21:31:46 ACERX kernel: [  504.798756] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 10 21:31:46 ACERX kernel: [  504.966739] wlan0: direct probe to AP 00:22:15:86:e4:b0 try 1
Aug 10 21:31:46 ACERX kernel: [  504.966765] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Aug 10 21:31:46 ACERX kernel: [  504.971211] wlan0: direct probe to AP 00:22:15:86:e4:b0 try 1
Aug 10 21:31:46 ACERX kernel: [  504.971252] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Aug 10 21:31:46 ACERX kernel: [  504.971264] wlan0 direct probe responded
Aug 10 21:31:46 ACERX kernel: [  504.971268] wlan0: authenticate with AP 00:22:15:86:e4:b0
Aug 10 21:31:46 ACERX kernel: [  504.975560] wlan0: authenticated
Aug 10 21:31:46 ACERX kernel: [  504.975568] wlan0: associate with AP 00:22:15:86:e4:b0
Aug 10 21:31:46 ACERX kernel: [  504.975573] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
Aug 10 21:31:46 ACERX kernel: [  505.168130] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Aug 10 21:31:49 ACERX kernel: [  508.005435] wlan0: authenticate with AP 00:22:15:86:e4:b0
Aug 10 21:31:49 ACERX kernel: [  508.007624] wlan0: authenticate with AP 00:22:15:86:e4:b0
Aug 10 21:31:49 ACERX kernel: [  508.013946] wlan0: authenticated
Aug 10 21:31:49 ACERX kernel: [  508.013952] wlan0: associate with AP 00:22:15:86:e4:b0
Aug 10 21:31:49 ACERX kernel: [  508.020220] wlan0: RX AssocResp from 00:22:15:86:e4:b0 (capab=0x411 status=0 aid=1)
Aug 10 21:31:49 ACERX kernel: [  508.020225] wlan0: associated
Aug 10 21:31:49 ACERX kernel: [  508.021947] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 10 21:31:50 ACERX dhclient: Internet Systems Consortium DHCP Client V3.1.1
Aug 10 21:31:50 ACERX dhclient: Copyright 2004-2008 Internet Systems Consortium.
Aug 10 21:31:50 ACERX dhclient: All rights reserved.
Aug 10 21:31:50 ACERX dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug 10 21:31:50 ACERX dhclient: 
Aug 10 21:31:50 ACERX dhclient: wmaster0: unknown hardware address type 801
Aug 10 21:31:50 ACERX avahi-daemon[2698]: Registering new address record for fe80::222:faff:fe04:f2fc on wlan0.*.
Aug 10 21:31:51 ACERX dhclient: wmaster0: unknown hardware address type 801
Aug 10 21:31:51 ACERX dhclient: Listening on LPF/wlan0/00:22:fa:04:f2:fc
Aug 10 21:31:51 ACERX dhclient: Sending on   LPF/wlan0/00:22:fa:04:f2:fc
Aug 10 21:31:51 ACERX dhclient: Sending on   Socket/fallback
Aug 10 21:31:51 ACERX dhclient: DHCPREQUEST of 192.168.0.198 on wlan0 to 255.255.255.255 port 67
Aug 10 21:31:58 ACERX dhclient: DHCPREQUEST of 192.168.0.198 on wlan0 to 255.255.255.255 port 67
Aug 10 21:31:59 ACERX kernel: [  518.368108] wlan0: no IPv6 routers present
Aug 10 21:32:08 ACERX dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Aug 10 21:32:13 ACERX dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 10 21:32:21 ACERX dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Aug 10 21:32:30 ACERX dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Aug 10 21:32:51 ACERX dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Aug 10 21:33:09 ACERX dhclient: No DHCPOFFERS received.
Aug 10 21:33:09 ACERX dhclient: Trying recorded lease 192.168.0.198
Aug 10 21:33:09 ACERX avahi-daemon[2698]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.198.
Aug 10 21:33:09 ACERX avahi-daemon[2698]: New relevant interface wlan0.IPv4 for mDNS.
Aug 10 21:33:09 ACERX avahi-daemon[2698]: Registering new address record for 192.168.0.198 on wlan0.IPv4.
Aug 10 21:33:12 ACERX avahi-daemon[2698]: Withdrawing address record for 192.168.0.198 on wlan0.
Aug 10 21:33:12 ACERX avahi-daemon[2698]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.198.
Aug 10 21:33:12 ACERX avahi-daemon[2698]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 10 21:33:12 ACERX avahi-autoipd(wlan0)[4245]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Aug 10 21:33:12 ACERX avahi-autoipd(wlan0)[4245]: Successfully called chroot().
Aug 10 21:33:12 ACERX avahi-autoipd(wlan0)[4245]: Successfully dropped root privileges.
Aug 10 21:33:12 ACERX avahi-autoipd(wlan0)[4245]: Starting with address 169.254.10.215
Aug 10 21:33:17 ACERX avahi-autoipd(wlan0)[4245]: Callout BIND, address 169.254.10.215 on interface wlan0
Aug 10 21:33:17 ACERX avahi-daemon[2698]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.10.215.
Aug 10 21:33:17 ACERX avahi-daemon[2698]: New relevant interface wlan0.IPv4 for mDNS.
Aug 10 21:33:17 ACERX avahi-daemon[2698]: Registering new address record for 169.254.10.215 on wlan0.IPv4.
Aug 10 21:33:21 ACERX avahi-autoipd(wlan0)[4245]: Successfully claimed IP address 169.254.10.215
Aug 10 21:33:21 ACERX dhclient: No working leases in persistent database - sleeping.

```

---

### Post by roopeshvaddepally on 2009-11-06
I have the same problem.
I am using Ubuntu 9.10
Wireless card is Intel Wifi 5100 AGN
I am using Wicd, tried Network Manager earlier.
Tried installing linux-backports-generic-karmik
then tried installing compat-wireless drivers too. Nothing is working.

Can someone help me.
I am shifting from ubuntu to windows to get the answers, and is really frustrating.

---

