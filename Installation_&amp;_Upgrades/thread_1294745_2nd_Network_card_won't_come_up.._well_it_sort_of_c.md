---
title: "2nd Network card won't come up.. well it sort of comes up"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by abasel on 2009-10-18
Just to give you the background, I am doing the following install [https://help.ubuntu.com/community/WifiDocs/CoovaChilli]("https://help.ubuntu.com/community/WifiDocs/CoovaChilli")

My network is defined as follows (for the final install the cards will be on different networks)
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.110.40
        netmask 255.255.255.0
        network 192.168.110.0
        broadcast 192.168.110.255
        gateway 192.168.110.254
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.100.1
        dns-search baselmania.private

auto eth1
iface eth1 inet static
        address 192.168.110.41
        netmask 255.255.255.0
        network 192.168.110.0
        broadcast 192.168.110.255
        gateway 192.168.110.254
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.100.1
        dns-search baselmania.private
```

ifconfig returns

```
eth0      Link encap:Ethernet  HWaddr 00:0e:2e:07:36:ee
          inet addr:192.168.110.40  Bcast:192.168.110.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe07:36ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:199103 (199.1 KB)  TX bytes:160122 (160.1 KB)
          Interrupt:19 Base address:0xcc00

eth1      Link encap:Ethernet  HWaddr 00:0b:6a:ce:86:ec
          inet6 addr: fe80::20b:6aff:fece:86ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:132048 (132.0 KB)  TX bytes:1963 (1.9 KB)
          Interrupt:17 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:841 (841.0 B)  TX bytes:841 (841.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:192.168.110.40  P-t-P:192.168.110.40  Mask:255.255.255.0
          UP POINTOPOINT RUNNING  MTU:1500  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:14148 (14.1 KB)  TX bytes:0 (0.0 B)

```

As you can see no IP. When I use DHCP I get an IP but the machine is then no longer reachable.

---

