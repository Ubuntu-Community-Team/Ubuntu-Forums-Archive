---
title: "Netboot install help--dchp3-server failing!"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by Brunellus on 2006-02-09
THE SITUATION:
I want to use my computer (funes) to serve a boot image to a new computer (nova).  

Funes has 2 network interfaces:  ath0 (active) and eth0 (currently unused).

THE PLAN:

Follow the directions in this howto:

[https://wiki.ubuntu.com/Installation/LocalNet](https://wiki.ubuntu.com/Installation/LocalNet)

Funes will be the dhcp server for a new local network, on which nova is the only host connected.  The network will be on funes' eth0.

THE PROBLEM

after installation, dhcp3-server fails:

starting DHCP server.....[fail]

restarting doesn't help. 

This is the text of /etc/dhcp3/dhcpd.conf:

```
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

#host pxeinstall {
#  hardware ethernet [mac-address of pxe networkcard without brackets];
#  fixed-address 10.0.0.16;
#  filename "pxelinux.0";
#}


filename="ubuntu/install/netboot/pxelinux.0";
#subnet 192.168.1.0  netmask 255.255.255.0 {
#        range 192.168.1.10 192.168.1.254;
#	option routers 192.168.1.1;
#	option broadcast-address 192.168.1.255;
#         }

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}
#subnet 192.168.1.0 netmask 255.255.255.0 {
#  range 192.168.1.2 192.168.1.99;
#  option routers 192.168.1.1;
#  option broadcast-address 192.168.1.255;
#}

#host pxeinstall {
#  fixed-address 192.168.1.2;
#  filename "pxelinux.0";
#   filename="ubuntu/install/netboot/pxelinux.0"
#}

# eth0 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
}



```

these are the contents of /etc/default/dchp3-server

```
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"

```

help!

---

### Post by polymeer on 2006-03-04
I had to change the IP address in /etc/ltsp/dhcpd.conf because my machine was in 192.168.1.x instaed of 192.168.0.x

---

