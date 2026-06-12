---
title: "wireless again - WRT54G"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by hoodwink on 2005-12-26
I'm most of the way to success with my laptop connecting through a WRT54G wireless; close, but no cigar.  First the setup:

hp ze4630us with dapper and latest upgrades (all else other than wireless working well.
cable <-> modem <->router <-> ...
   <-> (1) hardwired connection (linux desktop with dapper)
   <-> (2) hardwired conection (WinXP)
   <-> (3) hardwired connection to WRT54G

Other Windows laptops can connect to the internet successfully via wireless connection to the WRT54G. 

I have installed the necessary ndiswrapper / driver setup for the ze4630us (it uses a broadcom chip that is identical to a Dell Truemobile .... in the ndiswrapper database. The module generated ok, and modprobe ndiswrapper is successful. I've put the following in /etc/network/interfaces.

```

# wireless
auto wlan0
iface wlan0 inet dhcp
netmask 255.255.255.0
network 192.168.2.2
broadcast 192.168.2.255
gateway 192.168.2.1 

```

ifconfig, iwconfig show typical values, but dhcp is unable to obtain a lease. I get the following:

```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

/etc/dhcp3/dhclient.conf line 1: no option named dhcp-class-identifier
send dhcp-class-identifier "NetcfgDHClient"
     ^
/etc/dhcp3/dhclient.conf line 1: semicolon expected.

^
Listening on LPF/wlan0/00:90:4b:4d:72:91
Sending on   LPF/wlan0/00:90:4b:4d:72:91
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

The dhclient.conf file is not something that I have changed.

Using wireless_tools, if get data that shows the interface is working (values that can only come from the WRT54G. So the missing piece is getting hcp to obtain a lease.

Any help is appreciated.

Also, once working, I need to know how to enable the wireless connection selectively at boot time. Sometimes I will use a wired connection and sometimes wireless. When running Gentoo, there was a procedure that used a boot parameter to control the selection (ie boot with one grub selection for wired and aother for wireless). I'm not familiar with the Debian style networking setup to know how to do this on Ubuntu.

TIA,

---

