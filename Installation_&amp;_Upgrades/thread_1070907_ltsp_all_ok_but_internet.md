---
title: "ltsp all ok but internet"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by amazilia on 2009-02-15
Hi,

I just installed an ubuntu from the alternate cd (8.10) with the LTSP option (F4 at startup)

during the installation, I was asked for the network card to connect the server to the net using DHCP, it went fine (I was able during install to see some files being downloaded).

at the end the thin client system was build and compressed, such as on : [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

once the server restarted I have been able to get routing from the second network card. I got an address for a PC runing ubuntu8.10 and I have been able to boot the same PC from the network card and able to start a session.

So LTSP seems to work fine.

Now I cannot go on the internet using the server or a thin client or a PC.

ifconfig gives me the same address (192.168.0.254) for both cards on the server, whereas the internet card should give something like 10.0.0.x

Thanks for your help

Philippe


edit : this could help

```
ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:18:71:ea:38:c3  
          inet adr:192.168.0.254  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::218:71ff:feea:38c3/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:31118 erreurs:0 :0 overruns:0 frame:0
          TX packets:42635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:100 
          Octets reçus:4024299 (4.0 MB) Octets transmis:47509290 (47.5 MB)
          Mémoire:fdee0000-fdf00000 

eth1      Link encap:Ethernet  HWaddr 00:1a:4b:fe:48:c4  
          inet adr:192.168.0.254  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::21a:4bff:fefe:48c4/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:25 erreurs:0 :0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:4670 (4.6 KB) Octets transmis:7949 (7.9 KB)
          Interruption:16 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:21998 erreurs:0 :0 overruns:0 frame:0
          TX packets:21998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:18329119 (18.3 MB) Octets transmis:18329119 (18.3 MB)

```

```
route
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         servbib.local   0.0.0.0         UG    0      0        0 eth1
```

```
more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
#iface eth1 inet dhcp

auto eth0
iface eth0 inet static
    address 192.168.0.254
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
```

```
more /etc/ltsp/dhcpd.conf 
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```

---

### Post by amazilia on 2009-02-16
Hi,

I gave up.


I installed 8.04 without any problem. Internet is back.


Philippe

---

