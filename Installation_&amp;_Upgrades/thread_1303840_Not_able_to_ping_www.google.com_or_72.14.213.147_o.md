---
title: "Not able to ping www.google.com or 72.14.213.147 or any external sites from pc"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by anupindi007 on 2009-10-28
Hi,
[COLOR=Blue][COLOR=Red]**Problem: ** Not able to ping( [www.google.com]("http://www.google.com")  (but resolves ip  72.14.213.147)  or  [/COLOR] [/COLOR][COLOR=Red]Browse any external sites.[/COLOR]

a. able to[COLOR=Blue] ping[/COLOR] from [COLOR=Blue]**pc**[COLOR=Black] to[/COLOR] Server -** eth0**[/COLOR] 
b. able to[COLOR=Blue] ping[/COLOR] from [COLOR=Blue]**pc** [COLOR=Black]to[/COLOR] Server -[B] eth1
[/B][COLOR=Black]c. [COLOR=Blue]able to browse[/COLOR]** Internet** from [B][COLOR=Blue]Server
d. [/COLOR][/B][COLOR=Blue]while trying to ping [www.google.com]("http://www.google.com")   [/COLOR][B][COLOR=Blue]
 [COLOR=Black]--says: [/COLOR][/COLOR][/B][COLOR=DarkOrchid]pinging [www.1.google.com]("http://www.1.google.com")[72.14.213.103] with 32 bytes of data: Request time out.[/COLOR][B][COLOR=Blue]


[/COLOR][/B][/COLOR] [/COLOR]**Setup:**
[COLOR=Blue]PC[/COLOR] --> [COLOR=Blue]Router[/COLOR] > [COLOR=Blue]Server[/COLOR](eth1(internal) ->eth0(external), [COLOR=Blue]DNS/firewall[/COLOR] -->[COLOR=Blue] Internet[/COLOR]

[COLOR=Blue][COLOR=Black]
**Study Notes:**
Server eth0 IP: 10.10.10.95 subnet 255.255.255.0
Server eth1 IP: 10.5.5.1      [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]subnet 255.255.255.224[/COLOR][/COLOR]
[COLOR=Blue][COLOR=Black]
Router ip external:  [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]10.5.5.10[/COLOR][/COLOR]
[COLOR=Blue][COLOR=Black]Router ip internal:   172.16.2.1
Router Default GW : [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]10.5.5.1[/COLOR][/COLOR]
[COLOR=Blue][COLOR=Black]
PC IP: [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]172.16.2.10[/COLOR][/COLOR]
[COLOR=Blue][COLOR=Black]
**# route -n**
Kernel IP routing table
Destination ----     Gateway         [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]Genmask         [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]------------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]Flags Metric Ref    Use [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]Iface
10.5.5.0   [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]--         0.0.0.0         [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]255.255.255.224 [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]U     0      0        0 [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----------------------- [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]eth1
10.1.10.0 [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]--        0.0.0.0         [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]255.255.255.0     [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----U     0      0        0 [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----------------------- [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]eth0
169.254.0.0 [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]-[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]      0.0.0.0         [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]-----[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]255.255.0.0        [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]-----------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]U     1000   0        0 [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]------------------ [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]eth0
0.0.0.0           [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]--------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]10.1.10.1[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]---[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]0.0.0.0              [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]------------------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]UG    100    0        0 [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]------------------ [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]eth0

**#cat /etc/resolv.conf**
nameserver 10.1.10.1


**# cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 10.5.5.1
netmask 255.255.255.224

**#cat /etc/dhcp3/dhcpd.conf **
...
A slightly different configuration for an internal subnet.
subnet 10.5.5.0 netmask 255.255.255.224 {
  range 10.5.5.10 10.5.5.15;
  option domain-name-servers 10.10.10.1;
#  option domain-name "internal.example.org";
#   option routers ;
#  option broadcast-address 10.5.5.31;
  default-lease-time 864600;
  max-lease-time 60480;
}

[/COLOR][/COLOR]any help is very much appreciated.
Thanks,
Srinivas

---

### Post by anupindi007 on 2009-10-28
Updates: 
From pc while typing > [COLOR=Blue]**nslookup [www.google.com]("http://www.google.com")**[/COLOR]
[COLOR=Purple][COLOR=DarkOrchid]*** Can't find server name for address 10.5.5.1 : Non-existent domain
*** Default servers are not available
Server: Unknown
Address: 10.5.5.1

Non-authoritative answer:
Name: [www.1.google.com]("http://www.1.google.com")
Addresses: 74.125.127.147,[/COLOR][/COLOR][COLOR=DarkOrchid]72.14.213.104,[/COLOR][COLOR=Purple][COLOR=DarkOrchid]...
Aliases: [www.google.com]("http://www.google.com")[/COLOR]

[COLOR=Black]> [COLOR=Blue]ping [www.google.com]("http://www.google.com")[/COLOR] [/COLOR]
[/COLOR][COLOR=DarkOrchid]Pinging [www.1.google.com]("http://www.1.google.com") [72.14.213.104] with 32bytes of data:
Request timed out.
Request timed out.[/COLOR]

[B][COLOR=Blue]Note:
a. [/COLOR][/B][COLOR=DarkOrchid][COLOR=Black]10.5.5.1 is Server eth1 local ip and i am able to ping too.

b. DNS server is running on 10.5.5.1(on eth1) and **where is the problem ???:(**
i[COLOR=Blue] # sh dnsmasq status[/COLOR]
[COLOR=DarkOrchid] * Checking DNS forwarder and DHCP server dnsmasq                                                * (running)[/COLOR]

ii  [COLOR=Blue]#sh dnsmasq stop ; ping [www.yahoo.com](www.yahoo.com) [/COLOR]
 [COLOR=DarkOrchid]Pinging request could not find host [www.yahoo.com](www.yahoo.com) . Please check the name and try again.
[/COLOR]
iii [/COLOR][/COLOR][COLOR=Blue]#sh dnsmasq start; [/COLOR][COLOR=DarkOrchid][COLOR=Black][COLOR=Blue] ping [www.yahoo.com](www.yahoo.com)[/COLOR]
[/COLOR][/COLOR][COLOR=DarkOrchid][COLOR=Black] [COLOR=DarkOrchid]Pinging [/COLOR][/COLOR][/COLOR][COLOR=DarkOrchid][COLOR=Black][COLOR=DarkOrchid]www-real.wa1.b.yahoo.com [209.131.36.158] with 32 bytes of data: ...[/COLOR]

[/COLOR][/COLOR]

---

