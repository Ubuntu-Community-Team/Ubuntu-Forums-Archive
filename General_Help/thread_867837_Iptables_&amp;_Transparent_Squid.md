---
title: "Iptables &amp; Transparent Squid"
date: 2008-07-23
forum: General Help
---

### Post by flokky on 2008-07-23
I'm using iptables to calculate the amount of transferred data are using on a monthly basis. When my users go over a certain amount of bytes, I add a firewall rule which prevent them of accessing the internet. That's working great.

At this point, however, I would like to incorporate Squid, so all website from my users are cached in the proxy. I tried altering my script, but haven't succeeded yet. 

Now I'm facing two problems: either the clients cannot surf the web or squid isn't used to cache. Plus when I do the math and calculate the exact amount of data went through the firewall, this is not correct.

This is my script: 
[PHP]#!/bin/sh 
# squid server IP 
SQUID_SERVER=\"192.168.0.100\" 
# Interface connected to Internet 
INTERNET=\"eth0\" 
# Interface connected to LAN 
LAN_IN=\"eth1\" 
# Squid port 
SQUID_PORT=\"3128\" 

# Clean old firewall 
iptables -F 
iptables -Z 
iptables -X 
iptables -t nat -F 
iptables -t nat -X 
iptables -t mangle -F 
iptables -t mangle -X 

# Load IPTABLES modules for NAT and IP conntrack support 
modprobe ip_tables 
modprobe iptable_nat 
modprobe ip_nat_irc 
modprobe ip_conntrack 
modprobe ip_conntrack_ftp 
modprobe ip_nat_ftp 

echo \"Done loading modules...\\n\" 

echo \" Enabling forwarding..\" 
echo 1 > /proc/sys/net/ipv4/ip_forward 

# Setting default filter policy 
iptables -P INPUT ACCEPT 
iptables -P OUTPUT ACCEPT 

iptables -N accounting-in 
iptables -N accounting-out 

iptables -A FORWARD -i $INTERNET -o $LAN_IN -j accounting-in 

iptables -A FORWARD -i $LAN_IN -o $INTERNET -j accounting-out 

iptables -A accounting-out -s 192.168.0.101 -m mac --mac-source 00:19:B9:52:46:4A -j RETURN 
iptables -A accounting-out -s 192.168.0.102 -m mac --mac-source 00:90:4B:B0:01:A6 -j RETURN 

iptables -A accounting-out -j LOG --log-prefix \"Unknown mac:\" --log-ip-options 
iptables -A accounting-out -j REJECT 

iptables -A accounting-in -d 192.168.0.101 -j RETURN 
iptables -A accounting-in -d 192.168.0.102 -j RETURN 

iptables -A accounting-in -j LOG --log-prefix \"Unknown ip: \" --log-ip-options 
iptables -A accounting-in -j DROP 

iptables -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port 3128
iptables -t nat -A POSTROUTING -o $INTERNET -j MASQUERADE 
[/PHP]

It might have something to do with the fact I have to chain other rule, but I don't know how to persue this. Can someone help? Thx

---

