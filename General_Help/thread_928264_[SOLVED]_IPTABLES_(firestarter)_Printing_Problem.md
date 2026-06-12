---
title: "[SOLVED] IPTABLES (firestarter) Printing Problem"
date: 2008-09-23
forum: General Help
---

### Post by concord on 2008-09-23
I have a cups server (7.04) which works perfectly with both of my Ubuntu 8.04 Desktops.  One of the desktops (mine) does not see the printers as long as the firewall is on.

Server IP 192.168.1.107 (hostname:hp)
My workstation IP 192.168.1.109

I've enabled connections to port 631 from anywhere
I've turned off ICMP filtering
I've allowed ANY connections from 192.168.1.107

As long as the firewall is up I cannot see my printers.  If I turn it off - there they be!

Here is the output of iptables -L, does anyone have any suggestions?
```
root@s170:~# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  hummingbird          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  hummingbird          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  s170                 hummingbird         tcp dpt:domain 
ACCEPT     udp  --  s170                 hummingbird         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  hp                   anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:49152 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:49152 
ACCEPT     tcp  --  hp                   anywhere            tcp dpt:ipp 
ACCEPT     udp  --  hp                   anywhere            udp dpt:ipp 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
root@s170:~# 
```

Please let me know if you need more output.  Needless to say, since the server works fine without the firewall active on 192.168.1.109, it is configured properly.

Any ideas?  Thanks in advance.

- Frank

---

### Post by concord on 2008-09-23
Just after posting this problem I discovered the solution.  Apparently Firestarter was configured to block broadcasts from the external network.  I unchecked this box and it solved the issue.

[IMG]http://www.concordsystems.com/images/Screenshot-Preferences.png[/IMG]

Doh!

> **concord said:**
> I have a cups server (7.04) which works perfectly with both of my Ubuntu 8.04 Desktops.  One of the desktops (mine) does not see the printers as long as the firewall is on.

Server IP 192.168.1.107 (hostname:hp)
My workstation IP 192.168.1.109

I've enabled connections to port 631 from anywhere
I've turned off ICMP filtering
I've allowed ANY connections from 192.168.1.107

As long as the firewall is up I cannot see my printers.  If I turn it off - there they be!


Please let me know if you need more output.  Needless to say, since the server works fine without the firewall active on 192.168.1.109, it is configured properly.

Any ideas?  Thanks in advance.

- Frank

---

