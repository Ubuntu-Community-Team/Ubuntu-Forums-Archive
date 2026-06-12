---
title: "Ltsp 8.10"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by RandallHamm on 2009-01-20
Installed 8.10 LTSP from Alternate cd to HD1. Server has two NICs-one on motherboard and one PCI slot.
Upon install I can attach client with PXE, but the other NIC to the router / Internet will not connect.

The same hardware connects correctly to both NICs (router switch and thin client switch) with LTSP 8.04 on HD0 so I do not suspect a hardware issue for now.

ETH0 and ETH1 are set to Automatic even after changing interfaces and dhcpd.conf files. And now neither NIC connects.

[http://ubuntuforums.org/showthread.p...highlight=ltsp](http://ubuntuforums.org/showthread.p...highlight=ltsp)

<<<>>> gksudo "gedit /etc/network/interfaces"

# The loopback network interface

auto lo

iface lo inet loopback



# The primary network interface

auto eth0

iface eth0 inet static

address 192.168.0.140

netmask 255.255.255.0

network 192.168.0.0

broadcast 192.168.0.255

gateway 192.168.0.1

# dns-* options are implemented by the resolvconf package, if installed

dns-nameservers 192.168.0.1



# The secondary network interface

auto eth1

iface eth1 inet static

address 192.168.1.1

netmask 255.255.255.0

network 192.168.1.0

broadcast 192.168.1.255

# dns-* options are implemented by the resolvconf package, if installed

dns-nameservers 192.168.0.1
<<<>>>

also

<<<>>> gksudo "gedit /etc/ltsp/dhcpd.conf"
#

# Default LTSP dhcpd.conf config file.

#



authoritative;



subnet 192.168.1.0 netmask 255.255.255.0 {

range 192.168.1.5 192.168.1.20;

option domain-name "*";

option domain-name-servers 192.168.1.1;

option broadcast-address 192.168.1.255;

option routers 192.168.1.1;

# next-server 192.168.0.254;

# get-lease-hostnames true;

option subnet-mask 255.255.255.0;

option root-path "/opt/ltsp/i386";

if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {

filename "/ltsp/i386/pxelinux.0";

} else {

filename "/ltsp/i386/nbi.img";

}

}
<<>>

Also, is the a way to get Windows command "ipconfig /all" data in Ubuntu?

How can one determine which NIC is eth0 or eth1?

Nu2U,
Randall

---

