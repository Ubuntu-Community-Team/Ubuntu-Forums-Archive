---
title: "eth1 receives, no transmit."
date: 2013-06-30
forum: Hardware
---

### Post by hawaiiman on 2013-06-30
I have 10.04 running on a school server. Things worked fine for 6 months, then eth1 stopped working so LAN has no web access. eth0 is dhcp from adsl router with range limited to 192.168.1.10. eth1 is static at 10.10.0.1 255.255.255.0 . I have made a couple of attempts to add network firewall, and suspect that ip tables rules have gotten messed up. I purged cherokee/apache and webmin.  When the server initially starts, eth1 will receive ok and transmit a little, but then quickly shuts down transmit of packets. LAN hosts (windows) ipconfig /all lists no gateway and a 169...... ip number instead of 10.10.0.10-10.10.0.150.

---

### Post by Kujua on 2013-07-01
Can you flush all iptables rules and see if that works? If it does then we can check what's wrong with your firewall.

```

iptables -F
iptables -F -t nat

```

---

### Post by hawaiiman on 2013-07-01
Good idea. FYI eth0 is working both ways. I have another project I'm doing to stream a live webcam feed from my laptop to our website. I have added a rule forwarding to eth0 this was required to get our LAN  on eth1 10.10.0.1 to access the internet. I'm at home right now. nearly bedtime here (GMT +7 hours). I'll get on the server tomorrow. In the mean time what is the next step after flushing so I can report back with some results?

---

### Post by Kujua on 2013-07-01
If you are sure that the problem is caused by the firewall rules, post them here so that everyone can have a look:
```

iptables -L -nv
iptables -L -nv -t nat

```

If you have other working firewall rules which you don't want to loose, take a backup before you flush the rules:
```
iptables-save > rules
```
To restore the saved rules:
```
iptables-restore < rules
```

And after flushing the rules remember to add some required rules back. Otherwise internet access from LAN will fail. I forgot to mention this in my earlier post.
```

#flushing the existing rules
iptables -F
iptables -F -t nat

#Allow packets from eth1 destined to the server. Required for DHCP.
iptables -A INPUT -i eth1 -j ACCEPT

#Allow forwarding
iptables -A FORWARD -j ACCEPT

#Add the NAT rule
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```
With these rules in place you should be able to ping an IP address on the internet from a machine on LAN behind your server:
```
ping 8.8.8.8
```
If that is working, then we can discuss building your firewall.

---

### Post by hawaiiman on 2013-07-01
Thanks very much. Yes, the rules you listed are there, currently. Obviously, I am not qualified to be a net-admin, but I'm all the school has at this point. Our biggest issues, now that the network is fairly reliable, is control of student access. At first I thought a firewall was the answer. After a long process of formatting public clients, and installing fresh OS, I've discovered Deep Freeze. I think it will go a long way towards cleaning things up. I also am looking at Apache/Cherokee mostly for traffic management. A lightweight firewall is certainly important too. Just trying to give a broader view, as it seems that there are compatibility issues between certain packages. I'l be at school in a few hours and do as you suggest, then post results.

---

### Post by Kujua on 2013-07-02
Use UFW to setup firewall if you are not well-versed in iptables. Or GUFW if you need a GUI.

---

### Post by hawaiiman on 2013-07-02
done, and re-boot, but no change. BTW I also added eth3 which is currently named as the LAN interface in interfaces. I also entered 

iptables -A INPUT -i eth3 -j ACCEPT
I am actively receiving packets on eth3 from client, but after initial 14.1 bytes nothing is being transmitted. client is not getting ip

---

### Post by hawaiiman on 2013-07-02
As our no-ip service also stopped, I did a port check on "can you see me" shows port 80 and 22 not open, although both are forwarded for tcp/udp in router

---

### Post by Kujua on 2013-07-02
Can you post your firewall rules here?

> done, and re-boot, but no change.
Try without rebooting after you make changes to firewall rules as per previous posts. Because the rules will not be saved automatically.

---

### Post by hawaiiman on 2013-07-02
As our no-ip service also stopped, I did a port check on "can you see me" shows port 80 and 22 not open, although both are forwarded for tcp/udp in router

---

### Post by Kujua on 2013-07-02
"can you see me" will show only the open services, right? (correct me if i am wrong). In our case, with the rules we were trying out, we didn't yet open up any of our services to the internet(eth0). Allowing ports 80,22 to be forwarded through the router is different from accepting incoming connections on those ports. So they will not show up on "can you see me".

This is getting very confusing. Can you provide some more details:
1. Did the clients on LAN get IP from the DHCP server running on your ubuntu box(after making changes in firewall rules)?
2. Were they able to ping an IP (not a DNS name) on the internet?
3. What exactly is the role of the ubuntu box? From your previous posts, I guess that it is the gateway to internet and it is also the DHCP server. What else? What other services does the box provide?

---

### Post by hawaiiman on 2013-07-02
My sincere apologies for being confusing. Ok, aparently what I did at school today accomplished nothing as I rebooted after I flushed and re-entered the rules you provided. I didn't bring the machine home today, so try again with same routine tomorrow. 1. no (see above) 2. no (see above) 3right now the box does nothing. it has been working fine for six months prior. It is getting dhcp from adsl modem router, then fiber converter modem to fiber line. Box hosts a simple website, no email service, we have a samba share for clients, DHCP is dealt to LAN, it also has a dns cache set up. As far as I know there is no firewall, currently running. It is also an ssh2 server. It has DUC software to notify No-ip of current ip#. Output I posted was at end of day today iptables -L

---

### Post by hawaiiman on 2013-07-02
I don't see the output I posted.

---

### Post by hawaiiman on 2013-07-03
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source

---

### Post by hawaiiman on 2013-07-03
ok, that was "before" purging again. purged again and entered listed rules. result: same as before. client send packets, but does not receive ip . ping from client 10 10.10.0.1 "destination host unreachable"
iptables -L  yields Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain ufw-after-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-after-output (0 references)
target     prot opt source               destination         

Chain ufw-before-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-before-output (0 references)
target     prot opt source               destination         

Chain ufw-reject-forward (0 references)
target     prot opt source               destination         

Chain ufw-reject-input (0 references)
target     prot opt source               destination         

Chain ufw-reject-output (0 references)
target     prot opt source               destination         

Chain ufw-track-input (0 references)
target     prot opt source               destination         

Chain ufw-track-output (0 references)
target     prot opt source               destination

---

### Post by hawaiiman on 2013-07-03
iptables -L -nv
Chain INPUT (policy ACCEPT 33489 packets, 9385K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 8586 packets, 1229K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (0 references)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by hawaiiman on 2013-07-03
iptables -L -nv -t nat
Chain PREROUTING (policy ACCEPT 21060 packets, 1702K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 2016 packets, 174K bytes)
 pkts bytes target     prot opt in     out     source               destination         
  106  6706 MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 2299 packets, 217K bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by hawaiiman on 2013-07-03
iptables -L -nv -t nat
Chain PREROUTING (policy ACCEPT 21060 packets, 1702K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 2016 packets, 174K bytes)
 pkts bytes target     prot opt in     out     source               destination         
  106  6706 MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 2299 packets, 217K bytes)
 pkts bytes target     prot opt in     out     source               destination         
root@JPRSchool:~# iptables -A INPUT -i eth3 -j ACCEPT
root@JPRSchool:~# iptables -L -nv -t nat
Chain PREROUTING (policy ACCEPT 21632 packets, 1755K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 2035 packets, 176K bytes)
 pkts bytes target     prot opt in     out     source               destination         
  174 12189 MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 2386 packets, 225K bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by hawaiiman on 2013-07-03
should the "MASQUERADE" rule list the subnet and range of the LAN?

---

### Post by hawaiiman on 2013-07-03
BTW I believe I mentioned before there are 2 ethernet cards, eth1 and eth3 as well as mainboard eth0. Both are installed. but currently
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.255.255.0

# The primary network interface
auto eth0
iface eth0 inet dhcp
gateway 192.168.1.1

# The LAN interface
auto eth3
iface eth3 inet static
address 10.10.0.1
netmask 255.255.255.0

---

### Post by hawaiiman on 2013-07-03
I enabled ufw
ufw status
Status: active

To                         Action      From
--                         ------      ----
67                         DENY        Anywhere
22                         ALLOW       Anywhere
80                         ALLOW       Anywhere

---

### Post by hawaiiman on 2013-07-03
I enabled ufw
ufw status
Status: active

To                         Action      From
--                         ------      ----
67                         DENY        Anywhere
22                         ALLOW       Anywhere
80                         ALLOW       Anywhere

---

### Post by Kujua on 2013-07-03
> **hawaiiman said:**
> should the "MASQUERADE" rule list the subnet and range of the LAN?
No. Since eth0 is your uplink connection, we just have to say: masquerade everything that goes out of eth0 interface. Explicitly listing subnet is not required.

---

### Post by Kujua on 2013-07-03
>  client send packets, but does not receive ip. ping from client 10 10.10.0.1 "destination host unreachable"
You do not have any DROP rules, so firewall is not dropping anything. Sounds like DHCP server is not functioning correctly. That is why clients did not get IP.
Can you try with static IP configuration?

---

### Post by Kujua on 2013-07-03
> **hawaiiman said:**
> I enabled ufw
ufw status
Status: active

To                         Action      From
--                         ------      ----
67                         DENY        Anywhere
22                         ALLOW       Anywhere
80                         ALLOW       Anywhere
I don't use UFW myself, so I cannot help much with it. But you could give it a try since it simplifies matters. But first we need to confirm if it's only firewall which is having a problem. Since you are seeing issues even without any DROP rules.

---

### Post by hawaiiman on 2013-07-03
Yes. I don't believe it's a rules problem. Everything was going perfect, and then changed. It may have been when I did update/upgrade . Maybe network manager caused it? I've turned of network manager, but still no joy. It's just the end of my day here, and our times seem to be somewhat out of synch. I guess I'll pack the beast up and take it home. be back on in an hour or so.

---

### Post by hawaiiman on 2013-07-03
Ok. so what's next?

---

### Post by Kujua on 2013-07-03
I don't think network-manager is causing this issue. It just sets IP for the interfaces. To check the IP:
```
ifconfig eth1
```
If you don't give interface name, it will show all the interfaces. If interfaces are having IP addresss you have configured in netwok-manager, then no issues there.

Did you try with static IPs? We are still in square 1 :(
Since we are not sure if there is any issue with DHCP server configuration, configure IP addresses statically on the client.
for eg: server (eth1): 10.10.0.1   client conncted to eth1: 10.10.0.2.
Disable UFW for now. Flush the rules as in earlier posts.
Then from client: ping 10.10.0.1

Let's see how this goes. After you have executed ping a few times, post the output of  iptables -L -nv.

---

### Post by hawaiiman on 2013-07-03
ok, i removed eth1 from machine, entered eth3 in interfaces, flushed rules and re-entered, set client ip to 10.10.0.10 as dhcp range starts there. client can now ping 10.10.0.1, but not 8.8.8.8 (unreachable). ipconfig of client shows no default gateway.

---

### Post by hawaiiman on 2013-07-03
[https://help.ubuntu.com/10.04/serverguide/firewall.html......??](https://help.ubuntu.com/10.04/serverguide/firewall.html......??)

---

### Post by hawaiiman on 2013-07-03
iptables -L -nv
Chain INPUT (policy ACCEPT 172 packets, 53184 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           
 1751  157K ACCEPT     all  --  eth3   *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 163 packets, 27343 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:137 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:68 
    0     0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID limit: avg 3/min burst 10 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-reject-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain ufw-track-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:22 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:80 

Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by Kujua on 2013-07-04
> **hawaiiman said:**
> ok, i removed eth1 from machine, entered eth3 in interfaces, flushed rules and re-entered, set client ip to 10.10.0.10 as dhcp range starts there. client can now ping 10.10.0.1, but not 8.8.8.8 (unreachable). ipconfig of client shows no default gateway.

So now we are sure there is nothing wrong with your interfaces :).  The client is able to ping your server. If server is configured as the gateway on client, then ping 8.8.8.8 will also work - provided you have the masquerade rule set.

Now since we are sure that the server can receive and transmit without issues, you will have to check why they are not getting IP through DHCP. You dhcpd config perhaps?

---

### Post by hawaiiman on 2013-07-04
dnsmasq: failed to bind DHCP server socket: Address already in use
root@JPRSchool:~# iptables -L -nv -t nat
Chain PREROUTING (policy ACCEPT 3034 packets, 218K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 911 packets, 60611 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    7  1414 MASQUERADE  all  --  *      eth0    10.10.0.0/24         0.0.0.0/0           
  198 12487 MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 1116 packets, 74512 bytes)
 pkts bytes target     prot opt in     out     source               destinatio

---

### Post by hawaiiman on 2013-07-04
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.255.255.0

# The primary network interface
auto eth0
iface eth0 inet dhcp
gateway 192.168.1.1


# The LAN interface
auto eth3
iface eth3 inet static
address 10.10.0.1
netmask 255.255.255.0
gateway 192.168.1.10

---

### Post by Kujua on 2013-07-04
> dnsmasq: failed to bind DHCP server socket: Address already in use
Looks like there is another instance of dnsmasq running.

```
netstat -aup|grep bootp
```
What does this show?

---

### Post by hawaiiman on 2013-07-04
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.255.255.0

# The primary network interface
auto eth0
iface eth0 inet dhcp
gateway 192.168.1.1


# The LAN interface
auto eth3
iface eth3 inet static
address 10.10.0.1
netmask 255.255.255.0
gateway 192.168.1.10

---

### Post by hawaiiman on 2013-07-04
I was researching problems with dnsmasq. This command is suposed to identify the item causing such a conflict. Unfortunately the answer didn't show in red, but bootp in red seemed to be the response.

---

### Post by hawaiiman on 2013-07-04
I've spent some time checking various how to's concerning dnsmasq setup. I am intending it to be a dns cache and a dhcp server, and it functioned nicely for 6 months.

---

### Post by Kujua on 2013-07-04
> **hawaiiman said:**
> I was researching problems with dnsmasq. This command is suposed to identify the item causing such a conflict. Unfortunately the answer didn't show in red, but bootp in red seemed to be the response.
(Please post the output if possible)
So I am assuming there is another instance of dnsmasq running already which is bound to port 67 (bootps)? Did you check dnsmasq logs? Perhaps you could kill the running instance of dnsmasq and run a new one in debug mode (add flag -d).
Also can you post the dnsmasq configuration and the command used to run dnsmasq?

---

### Post by hawaiiman on 2013-07-04
I've spent some time checking various how to's concerning dnsmasq setup. I am intending it to be a dns cache and a dhcp server, and it functioned nicely for 6 months.

---

### Post by hawaiiman on 2013-07-04
I have no idea how to determine if another instance of dnsmasq is running.
```

#Never forward plain names (without a dot or domain part)
#domain-needed
#Never forward addresses in the non-routed address spaces.
#bogus-priv


# Uncomment this to filter useless windows-originated DNS requests
# which can trigger dial-on-demand links needlessly.
# Note that (amongst other things) this blocks all SRV requests,
# so don't use it if you use eg Kerberos, SIP, XMMP or Google-talk.
# This option only affects forwarding, SRV records originating for
# dnsmasq (via srv-host= lines) are not suppressed by it.
#filterwin2k

# Change this line if you want dns to get its upstream servers from
# somewhere other that /etc/resolv.conf
#resolv-file=

# By  default,  dnsmasq  will  send queries to any of the upstream
# servers it knows about and tries to favour servers to are  known
# to  be  up.  Uncommenting this forces dnsmasq to try each query
# with  each  server  strictly  in  the  order  they   appear   in
# /etc/resolv.conf
#strict-order

# If you don't want dnsmasq to read /etc/resolv.conf or any other
# file, getting its servers from this file instead (see below), then
# uncomment this.
#no-resolv

# If you don't want dnsmasq to poll /etc/resolv.conf or other resolv
# files for changes and re-read them then uncomment this.
#no-poll

# Add other name servers here, with domain specs if they are for
# non-public domains.
#server=/localnet/192.168.0.1

# Example of routing PTR queries to nameservers: this will send all 
# address->name queries for 192.168.3/24 to nameserver 10.1.2.3
#server=/3.168.192.in-addr.arpa/10.1.2.3

# Add local-only domains here, queries in these domains are answered
# from /etc/hosts or DHCP only.
#local=/localnet/

# Add domains which you want to force to an IP address here.
# The example below send any host in doubleclick.net to a local
# webserver.
#address=/doubleclick.net/127.0.0.1

# --address (and --server) work with IPv6 addresses too.
#address=/www.thekelleys.org.uk/fe80::20d:60ff:fe36:f83

# You can control how dnsmasq talks to a server: this forces 
# queries to 10.1.2.3 to be routed via eth1
# --server=10.1.2.3@eth1

# and this sets the source (ie local) address used to talk to
# 10.1.2.3 to 192.168.1.1 port 55 (there must be a interface with that
# IP on the machine, obviously).
# --server=10.1.2.3@192.168.1.1#55

# If you want dnsmasq to change uid and gid to something other
# than the default, edit the following lines.
#user=
#group=

# If you want dnsmasq to listen for DHCP and DNS requests only on
# specified interfaces (and the loopback) give the name of the
# interface (eg eth0) here.
# Repeat the line for more than one interface.
#interface=eth1
interface=eth3
# Or you can specify which interface _not_ to listen on
#except-interface=eth0
# Or which to listen on by address (remember to include 127.0.0.1 if
# you use this.)
listen-address= 127.0.0.1
listen-address= 10.10.0.1
# If you want dnsmasq to provide only DNS service on an interface,
# configure it as shown above, and then use the following line to
# disable DHCP on it.
#no-dhcp-interface=eth0

# On systems which support it, dnsmasq binds the wildcard address,
# even when it is listening on only some interfaces. It then discards
# requests that it shouldn't reply to. This has the advantage of
# working even when interfaces come and go and change address. If you
# want dnsmasq to really bind only the interfaces it is listening on,
# uncomment this option. About the only time you may need this is when
# running another nameserver on the same machine.
#bind-interfaces

# If you don't want dnsmasq to read /etc/hosts, uncomment the
# following line.
#no-hosts
# or if you want it to read another file, as well as /etc/hosts, use
# this.
#addn-hosts=/etc/banner_add_hosts

# Set this (and domain: see below) if you want to have a domain
# automatically added to simple names in a hosts-file.
#expand-hosts

# Set the domain for dnsmasq. this is optional, but if it is set, it
# does the following things.
# 1) Allows DHCP hosts to have fully qualified domain names, as long
#     as the domain part matches this setting.
# 2) Sets the "domain" DHCP option thereby potentially setting the
#    domain of all systems configured by DHCP
# 3) Provides the domain part for "expand-hosts"
#domain=thekelleys.org.uk

# Set a different domain for a particular subnet
#domain=wireless.thekelleys.org.uk,192.168.2.0/24

# Same idea, but range rather then subnet
#domain=reserved.thekelleys.org.uk,192.68.3.100,192.168.3.200

# Uncomment this to enable the integrated DHCP server, you need
# to supply the range of addresses available for lease and optionally
# a lease time. If you have more than one network, you will need to
# repeat this for each network on which you want to supply DHCP
# service.
dhcp-range=eth3,10.10.0.10,10.10.0.150,8h

# This is an example of a DHCP range where the netmask is given. This
# is needed for networks we reach the dnsmasq DHCP server via a relay
# agent. If you don't know what a DHCP relay agent is, you probably
# don't need to worry about this.
#dhcp-range=192.168.0.50,192.168.0.150,255.255.255.0,12h

# This is an example of a DHCP range with a network-id, so that
# some DHCP options may be set only for this network.
#dhcp-range=red,192.168.0.50,192.168.0.150

# Supply parameters for specified hosts using DHCP. There are lots
# of valid alternatives, so we will give examples of each. Note that
# IP addresses DO NOT have to be in the range given above, they just
# need to be on the same network. The order of the parameters in these
# do not matter, it's permissble to give name,adddress and MAC in any order

# Always allocate the host with ethernet address 11:22:33:44:55:66
# The IP address 192.168.0.60
#dhcp-host=11:22:33:44:55:66,192.168.0.60

# Always set the name of the host with hardware address
# 11:22:33:44:55:66 to be "fred"
#dhcp-host=11:22:33:44:55:66,fred

# Always give the host with ethernet address 11:22:33:44:55:66
# the name fred and IP address 192.168.0.60 and lease time 45 minutes
#dhcp-host=11:22:33:44:55:66,fred,192.168.0.60,45m

# Give a host with ethernet address 11:22:33:44:55:66 or
# 12:34:56:78:90:12 the IP address 192.168.0.60. Dnsmasq will assume
# that these two ethernet interfaces will never be in use at the same
# time, and give the IP address to the second, even if it is already
# in use by the first. Useful for laptops with wired and wireless
# addresses.
#dhcp-host=11:22:33:44:55:66,12:34:56:78:90:12,192.168.0.60

# Give the machine which says its name is "bert" IP address
# 192.168.0.70 and an infinite lease
#dhcp-host=bert,192.168.0.70,infinite

# Always give the host with client identifier 01:02:02:04
# the IP address 192.168.0.60
#dhcp-host=id:01:02:02:04,192.168.0.60

# Always give the host with client identifier "marjorie"
# the IP address 192.168.0.60
#dhcp-host=id:marjorie,192.168.0.60

# Enable the address given for "judge" in /etc/hosts
# to be given to a machine presenting the name "judge" when
# it asks for a DHCP lease.
#dhcp-host=judge

# Never offer DHCP service to a machine whose ethernet
# address is 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,ignore

# Ignore any client-id presented by the machine with ethernet
# address 11:22:33:44:55:66. This is useful to prevent a machine
# being treated differently when running under different OS's or
# between PXE boot and OS boot.
#dhcp-host=11:22:33:44:55:66,id:*

# Send extra options which are tagged as "red" to
# the machine with ethernet address 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,net:red

# Send extra options which are tagged as "red" to
# any machine with ethernet address starting 11:22:33:
#dhcp-host=11:22:33:*:*:*,net:red

# Ignore any clients which are specified in dhcp-host lines
# or /etc/ethers. Equivalent to ISC "deny unkown-clients".
# This relies on the special "known" tag which is set when 
# a host is matched.
#dhcp-ignore=#known

# Send extra options which are tagged as "red" to any machine whose
# DHCP vendorclass string includes the substring "Linux"
#dhcp-vendorclass=red,Linux

# Send extra options which are tagged as "red" to any machine one
# of whose DHCP userclass strings includes the substring "accounts"
#dhcp-userclass=red,accounts

# Send extra options which are tagged as "red" to any machine whose
# MAC address matches the pattern.
#dhcp-mac=red,00:60:8C:*:*:*

# If this line is uncommented, dnsmasq will read /etc/ethers and act
# on the ethernet-address/IP pairs found there just as if they had
# been given as --dhcp-host options. Useful if you keep
# MAC-address/host mappings there for other purposes.
#read-ethers

# Send options to hosts which ask for a DHCP lease.
# See RFC 2132 for details of available options.
# Common options can be given to dnsmasq by name: 
# run "dnsmasq --help dhcp" to get a list.
# Note that all the common settings, such as netmask and
# broadcast address, DNS server and default route, are given
# sane defaults by dnsmasq. You very likely will not need 
# any dhcp-options. If you use Windows clients and Samba, there
# are some options which are recommended, they are detailed at the
# end of this section.

# Override the default route supplied by dnsmasq, which assumes the
# router is the same machine as the one running dnsmasq.
# dhcp-option=3,1.2.3.4

# Do the same thing, but using the option name
# dhcp-option=option:router,1.2.3.4

# Override the default route supplied by dnsmasq and send no default
# route at all. Note that this only works for the options sent by
# default (1, 3, 6, 12, 28) the same line will send a zero-length option 
# for all other option numbers.
# dhcp-option=3

# Set the NTP time server addresses to 192.168.0.4 and 10.10.0.5
#dhcp-option=option:ntp-server,192.168.0.4,10.10.0.5

# Set the NTP time server address to be the same machine as
# is running dnsmasq
#dhcp-option=42,0.0.0.0

# Set the NIS domain name to "welly"
#dhcp-option=40,welly

# Set the default time-to-live to 50
#dhcp-option=23,50

# Set the "all subnets are local" flag
#dhcp-option=27,1

# Send the etherboot magic flag and then etherboot options (a string).
#dhcp-option=128,e4:45:74:68:00:00
#dhcp-option=129,NIC=eepro100

# Specify an option which will only be sent to the "red" network
# (see dhcp-range for the declaration of the "red" network)
# Note that the net: part must precede the option: part.
#dhcp-option = net:red, option:ntp-server, 192.168.1.1

# The following DHCP options set up dnsmasq in the same way as is specified
# for the ISC dhcpcd in
# [http://www.samba.org/samba/ftp/docs/textdocs/DHCP-Server-Configuration.txt](http://www.samba.org/samba/ftp/docs/textdocs/DHCP-Server-Configuration.txt)
# adapted for a typical dnsmasq installation where the host running
# dnsmasq is also the host running samba.
# you may want to uncomment some or all of them if you use 
# Windows clients and Samba.
#dhcp-option=19,0           # option ip-forwarding off
#dhcp-option=44,0.0.0.0     # set netbios-over-TCP/IP nameserver(s) aka WINS #server(s)
#dhcp-option=45,0.0.0.0     # netbios datagram distribution server
#dhcp-option=46,8           # netbios node type

# Send RFC-3397 DNS domain search DHCP option. WARNING: Your DHCP client
# probably doesn't support this......
#dhcp-option=option:domain-search,eng.apple.com,marketing.apple.com

# Send RFC-3442 classless static routes (note the netmask encoding)
#dhcp-option=121,192.168.1.0/24,1.2.3.4,10.0.0.0/8,5.6.7.8

# Send vendor-class specific options encapsulated in DHCP option 43. 
# The meaning of the options is defined by the vendor-class so
# options are sent only when the client supplied vendor class
# matches the class given here. (A substring match is OK, so "MSFT" 
# matches "MSFT" and "MSFT 5.0"). This example sets the
# mtftp address to 0.0.0.0 for PXEClients.
#dhcp-option=vendor:PXEClient,1,0.0.0.0

# Send microsoft-specific option to tell windows to release the DHCP lease
# when it shuts down. Note the "i" flag, to tell dnsmasq to send the
# value as a four-byte integer - that's what microsoft wants. See
# [http://technet2.microsoft.com/WindowsServer/en/library/a70f1bb7-d2d4-49f0-96d6-4b7414ecfaae1033.mspx?mfr=true](http://technet2.microsoft.com/WindowsServer/en/library/a70f1bb7-d2d4-49f0-96d6-4b7414ecfaae1033.mspx?mfr=true)
#dhcp-option=vendor:MSFT,2,1i

# Send the Encapsulated-vendor-class ID needed by some configurations of
# Etherboot to allow is to recognise the DHCP server.
#dhcp-option=vendor:Etherboot,60,"Etherboot"

# Send options to PXELinux. Note that we need to send the options even
# though they don't appear in the parameter request list, so we need
# to use dhcp-option-force here. 
# See [http://syslinux.zytor.com/pxe.php#special](http://syslinux.zytor.com/pxe.php#special) for details.
# Magic number - needed before anything else is recognised
#dhcp-option-force=208,f1:00:74:7e
# Configuration file name
#dhcp-option-force=209,configs/common
# Path prefix
#dhcp-option-force=210,/tftpboot/pxelinux/files/
# Reboot time. (Note 'i' to send 32-bit value)
#dhcp-option-force=211,30i

# Set the boot filename for netboot/PXE. You will only need 
# this is you want to boot machines over the network and you will need
# a TFTP server; either dnsmasq's built in TFTP server or an
# external one. (See below for how to enable the TFTP server.)
#dhcp-boot=pxelinux.0

# Boot for Etherboot gPXE. The idea is to send two different
# filenames, the first loads gPXE, and the second tells gPXE what to
# load. The dhcp-match sets the gpxe tag for requests from gPXE.
#dhcp-match=gpxe,175 # gPXE sends a 175 option.
#dhcp-boot=net:#gpxe,undionly.kpxe
#dhcp-boot=mybootimage
 
# Encapsulated options for Etherboot gPXE. All the options are
# encapsulated within option 175
#dhcp-option=encap:175, 1, 5b         # priority code
#dhcp-option=encap:175, 176, 1b       # no-proxydhcp 
#dhcp-option=encap:175, 177, string   # bus-id 
#dhcp-option=encap:175, 189, 1b       # BIOS drive code
#dhcp-option=encap:175, 190, user     # iSCSI username
#dhcp-option=encap:175, 191, pass     # iSCSI password

# Test for the architecture of a netboot client. PXE clients are
# supposed to send their architecture as option 93. (See RFC 4578)
#dhcp-match=peecees, option:client-arch, 0 #x86-32
#dhcp-match=itanics, option:client-arch, 2 #IA64
#dhcp-match=hammers, option:client-arch, 6 #x86-64
#dhcp-match=mactels, option:client-arch, 7 #EFI x86-64 

# Do real PXE, rather than just booting a single file, this is an
# alternative to dhcp-boot.
#pxe-prompt="What system shall I netboot?"
# or with timeout before first available action is taken:
#pxe-prompt="Press F8 for menu.", 60

# Available boot services. for PXE.
#pxe-service=x86PC, "Boot from local disk"

# Loads <tftp-root>/pxelinux.0 from dnsmasq TFTP server.
#pxe-service=x86PC, "Install Linux", pxelinux 

# Loads <tftp-root>/pxelinux.0 from TFTP server at 1.2.3.4.
# Beware this fails on old PXE ROMS.
#pxe-service=x86PC, "Install Linux", pxelinux, 1.2.3.4 

# Use bootserver on network, found my multicast or broadcast.
#pxe-service=x86PC, "Install windows from RIS server", 1

# Use bootserver at a known IP address.
#pxe-service=x86PC, "Install windows from RIS server", 1, 1.2.3.4

# If you have multicast-FTP available,
# information for that can be passed in a similar way using options 1
# to 5. See page 19 of
# [http://download.intel.com/design/archives/wfm/downloads/pxespec.pdf](http://download.intel.com/design/archives/wfm/downloads/pxespec.pdf)  

  
# Enable dnsmasq's built-in TFTP server
#enable-tftp

# Set the root directory for files availble via FTP.
#tftp-root=/var/ftpd

# Make the TFTP server more secure: with this set, only files owned by
# the user dnsmasq is running as will be send over the net.
#tftp-secure

# This option stops dnsmasq from negotiating a larger blocksize for TFTP 
# transfers. It will slow things down, but may rescue some broken TFTP
# clients.
#tftp-no-blocksize

# Set the boot file name only when the "red" tag is set.
#dhcp-boot=net:red,pxelinux.red-net

# An example of dhcp-boot with an external TFTP server: the name and IP
# address of the server are given after the filename.
# Can fail with old PXE ROMS. Overridden by --pxe-service.
#dhcp-boot=/var/ftpd/pxelinux.0,boothost,192.168.0.3

# Set the limit on DHCP leases, the default is 150
#dhcp-lease-max=150

# The DHCP server needs somewhere on disk to keep its lease database.
# This defaults to a sane location, but if you want to change it, use
# the line below.
#dhcp-leasefile=/var/lib/misc/dnsmasq.leases

# Set the DHCP server to authoritative mode. In this mode it will barge in
# and take over the lease for any client which broadcasts on the network,
# whether it has a record of the lease or not. This avoids long timeouts
# when a machine wakes up on a new network. DO NOT enable this if there's
# the slighest chance that you might end up accidentally configuring a DHCP
# server for your campus/company accidentally. The ISC server uses
# the same option, and this URL provides more information:
# [http://www.isc.org/index.pl?/sw/dhcp/authoritative.php](http://www.isc.org/index.pl?/sw/dhcp/authoritative.php)
#dhcp-authoritative

# Run an executable when a DHCP lease is created or destroyed.
# The arguments sent to the script are "add" or "del", 
# then the MAC address, the IP address and finally the hostname
# if there is one. 
#dhcp-script=/bin/echo

# Set the cachesize here.
cache-size=10000

# If you want to disable negative caching, uncomment this.
#no-negcache

# Normally responses which come form /etc/hosts and the DHCP lease
# file have Time-To-Live set as zero, which conventionally means
# do not cache further. If you are happy to trade lower load on the
# server for potentially stale date, you can set a time-to-live (in
# seconds) here.
#local-ttl=

# If you want dnsmasq to detect attempts by Verisign to send queries
# to unregistered .com and .net hosts to its sitefinder service and
# have dnsmasq instead return the correct NXDOMAIN response, uncomment
# this line. You can add similar lines to do the same for other
# registries which have implemented wildcard A records.
#bogus-nxdomain=64.94.110.11

# If you want to fix up DNS results from upstream servers, use the
# alias option. This only works for IPv4.
# This alias makes a result of 1.2.3.4 appear as 5.6.7.8
#alias=1.2.3.4,5.6.7.8
# and this maps 1.2.3.x to 5.6.7.x
#alias=1.2.3.0,5.6.7.0,255.255.255.0
# and this maps 192.168.0.10->192.168.0.40 to 10.0.0.10->10.0.0.40
#alias=192.168.0.10-192.168.0.40,10.0.0.0,255.255.255.0

# Change these lines if you want dnsmasq to serve MX records.

# Return an MX record named "maildomain.com" with target
# servermachine.com and preference 50
#mx-host=maildomain.com,servermachine.com,50

# Set the default target for MX records created using the localmx option.
#mx-target=servermachine.com

# Return an MX record pointing to the mx-target for all local
# machines.
#localmx

# Return an MX record pointing to itself for all local machines.
#selfmx

# Change the following lines if you want dnsmasq to serve SRV
# records.  These are useful if you want to serve ldap requests for
# Active Directory and other windows-originated DNS requests.
# See RFC 2782.
# You may add multiple srv-host lines.
# The fields are <name>,<target>,<port>,<priority>,<weight>
# If the domain part if missing from the name (so that is just has the
# service and protocol sections) then the domain given by the domain=
# config option is used. (Note that expand-hosts does not need to be
# set for this to work.)

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 289
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 289 (using domain=)
#domain=example.com
#srv-host=_ldap._tcp,ldapserver.example.com,389

# Two SRV records for LDAP, each with different priorities
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,1
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,2

# A SRV record indicating that there is no LDAP server for the domain
# example.com
#srv-host=_ldap._tcp.example.com

# The following line shows how to make dnsmasq serve an arbitrary PTR
# record. This is useful for DNS-SD. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for PTR records.)
#ptr-record=_http._tcp.dns-sd-services,"New Employee Page._http._tcp.dns-sd-services"

# Change the following lines to enable dnsmasq to serve TXT records.
# These are used for things like SPF and zeroconf. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for TXT records.)

#Example SPF.
#txt-record=example.com,"v=spf1 a -all"

#Example zeroconf
#txt-record=_http._tcp.example.com,name=value,paper=A4

# Provide an alias for a "local" DNS name. Note that this _only_ works
# for targets which are names from DHCP or /etc/hosts. Give host
# "bert" another name, bertrand
#cname=bertand,bert

# For debugging purposes, log each DNS query as it passes through
# dnsmasq.
#log-queries

# Log lots of extra information about DHCP transactions.
#log-dhcp

# Include a another lot of configuration options.
#conf-file=/etc/dnsmasq.more.conf
#conf-dir=/etc/dnsmasq.d
```

---

### Post by hawaiiman on 2013-07-04
I did another check, and I suspect dnsmasq may not be listning on the proper ports and/or that the proper ports may not be open. Can you help me with this? Is it correct to assume that if forwarding is working but dhcp is not that the ping results I'm seeing would result?

---

### Post by Kujua on 2013-07-04
> I have no idea how to determine if another instance of dnsmasq is running.
netstat command would've shown it.

Also, if this command shows a line with dnsmasq, it means there is an instance running:
```
ps -aux|grep dnsmasq
```

---

### Post by Kujua on 2013-07-04
> **hawaiiman said:**
> I did another check, and I suspect dnsmasq may not be listning on the proper ports and/or that the proper ports may not be open. Can you help me with this? Is it correct to assume that if forwarding is working but dhcp is not that the ping results I'm seeing would result?

No, if static IP address (including correct gateway) is configured on the client, then pinging an IP address (not DNS name) will work even if dnsmasq is not working.
Did netstat output show port 67 or bootps. If yes, then dnsmasq is listening on the right port.

BTW, I tried out your config file, and it is working for me. My client got IP from the server with that configuration.

Like I suggested earlier, can you run dnsmasq in debug mode (with -d flag)? Make the client request an IP from the server. Look at the logs that dnsmasq generates on the console (also please post).

---

### Post by hawaiiman on 2013-07-04
I did another check, and I suspect dnsmasq may not be listning on the proper ports and/or that the proper ports may not be open. Can you help me with this? Is it correct to assume that if forwarding is working but dhcp is not that the ping results I'm seeing would result?

---

### Post by hawaiiman on 2013-07-04
ps -aux|grep dnsmasq
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
dnsmasq   1214  0.0  0.1  23892  2032 ?        S    17:15   0:00 /usr/sbin/dnsmasq -x /var/run/dnsmasq/dnsmasq.pid -u dnsmasq -7 /etc/dnsmasq.d,.dpkg-dist,.dpkg-old,.dpkg-new
root      3413  0.0  0.0   7640   984 pts/0    S+   21:56   0:00 grep --color=auto dnsmasq

---

### Post by theDaveTheRave on 2013-07-04
Hawaiiman,

what exactly are you attempting to acheive here?

Are you using this system as your DHCP server such as....

ISP internet router ====> your box (192.168.1.10. eth0)
                                       your box =====> eth1 =>>> switch =>>>> rest of lan
                                       your box =====> eth2 =>>>switch =>>>> another lan (or fail over for first lan if going to same switch some how)

where < your box > is acting as your local router / dhcp.

if so this article on the [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) may help.

You also mention that the system had been working fine for 6 months.

does the problem coincide with an update ?
Do you update at the begining of each month (and 3 days ago was the first monday of the month !) - I know it sounds stupid, but i've had a security update kill my wifi (3 years ago now) and it still sits as having been a painful, but educational networking experience !


David.

---

### Post by Kujua on 2013-07-04
> **hawaiiman said:**
> ps -aux|grep dnsmasq
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
dnsmasq   1214  0.0  0.1  23892  2032 ?        S    17:15   0:00 /usr/sbin/dnsmasq -x /var/run/dnsmasq/dnsmasq.pid -u dnsmasq -7 /etc/dnsmasq.d,.dpkg-dist,.dpkg-old,.dpkg-new
root      3413  0.0  0.0   7640   984 pts/0    S+   21:56   0:00 grep --color=auto dnsmasq
Can you try running it like this, without the extra options, and see if client gets IP:
```
/usr/bin/dnsmasq -d
```

---

### Post by hawaiiman on 2013-07-04
ps -aux|grep dnsmasq
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
dnsmasq   1214  0.0  0.1  23892  2032 ?        S    17:15   0:00 /usr/sbin/dnsmasq -x /var/run/dnsmasq/dnsmasq.pid -u dnsmasq -7 /etc/dnsmasq.d,.dpkg-dist,.dpkg-old,.dpkg-new
root      3413  0.0  0.0   7640   984 pts/0    S+   21:56   0:00 grep --color=auto dnsmasq

---

### Post by hawaiiman on 2013-07-04
/usr/bin/dnsmasq -d
bash: /usr/bin/dnsmasq: No such file or directory

---

### Post by hawaiiman on 2013-07-04
@[**[COLOR=#000000]theDaveTheRave[/COLOR]**]("http://ubuntuforums.org/member.php?u=246735"). adsl over fiber router modem->eth0-> box->eth3 10.10.0.1-LAN 10.10.0.10-150 255.255.255.0. ->switch-> clients. Network topology-extended star. 192.168.1.1 deals dhcp to box, although range is restricted to 192.168.1.10. LAN is dealt dhcp by dnsmasq in the box and eth3 is assigned 10.10.0.1. the school has maybe 75 hosts. yes everything was good until update/upgrade, which hadn't been done in months(no sched).

---

### Post by hawaiiman on 2013-07-04
BTW, we're running the LAN off the router now. Unrestricted router DHCP to 192.168.1.10-150. I'm currently trying to broadcast a live webcam to a page on our webpage, which thgis server hosts.

---

### Post by darkod on 2013-07-04
Wow, this turned out into a huge discussion. :) Lets try to simplify it a little bit.

In very few words, what is exactly wrong?

The ubuntu server is not giving out dhcp leases? The clients receive dhcp address but can't go out to the internet through the server? What exactly fails?

And as for iptables vs ufw, I would stick with iptables regardless how new they are to you. ufw creates bunch of rules, and can get even more confusing even though it seems simple to start with. Especially for troubleshooting. Look how the ouput of iptables -L looks when using ufw. If using only iptables directly that output will have just few of your rules.

But in this case it doesn't seem like firewall issue, the above was only an observation and advice to stick with iptables directly if you can.

---

### Post by hawaiiman on 2013-07-04
BTW, we're running the LAN off the router now. Unrestricted router DHCP to 192.168.1.10-150. I'm currently trying to broadcast a live webcam to a page on our webpage, which thgis server hosts.

---

### Post by hawaiiman on 2013-07-04
@Darkod, the server just started breaking down. Hosts had no internet. We'd go back on the router for a few hours/days (I'm busy with other stuff) then turn server back on and no problem. Then that ended. All interfaces became one way. As it is now, eth0 works fine and server gets on the net. Right now I have another card in for LAN named eth3. It receives packets but after transmitting a few packets, it stops transmitting and clients get no ip. If I assign ip to client, i can ping 10.10.0.1 and 127.0.0.1 but nothing further.

---

### Post by hawaiiman on 2013-07-04
@Darkod, the server just started breaking down. Hosts had no internet. We'd go back on the router for a few hours/days (I'm busy with other stuff) then turn server back on and no problem. Then that ended. All interfaces became one way. As it is now, eth0 works fine and server gets on the net. Right now I have another card in for LAN named eth3. It receives packets but after transmitting a few packets, it stops transmitting and clients get no ip. If I assign ip to client, i can ping 10.10.0.1 and 127.0.0.1 but nothing further.

---

### Post by darkod on 2013-07-04
If you assing a correct manual (static) IP on a client, can it ping 10.10.0.1 and go on the internet?

---

### Post by Kujua on 2013-07-04
> **hawaiiman said:**
> /usr/bin/dnsmasq -d
bash: /usr/bin/dnsmasq: No such file or directory

sorry, typo: /usr/**sbin**/dnsmasqd -d

---

### Post by hawaiiman on 2013-07-04
/usr/sbin/dnsmasq -d 

dnsmasq: failed to bind DHCP server socket: Address already in use

---

### Post by hawaiiman on 2013-07-04
yes to 10.10.0.1  yes to 127.0.0.1  no to eth0 or past that

---

### Post by hawaiiman on 2013-07-04
# Configuration file for dnsmasq.
#
# Format is one option per line, legal options are the same
# as the long options legal on the command line. See
# "/usr/sbin/dnsmasq --help" or "man 8 dnsmasq" for details.

# The following two options make you a better netizen, since they
# tell dnsmasq to filter out queries which the public DNS cannot
# answer, and which load the servers (especially the root servers)
# uneccessarily. If you have a dial-on-demand link they also stop
# these requests from bringing up the link uneccessarily.

#Never forward plain names (without a dot or domain part)
#domain-needed
#Never forward addresses in the non-routed address spaces.
#bogus-priv


# Uncomment this to filter useless windows-originated DNS requests
# which can trigger dial-on-demand links needlessly.
# Note that (amongst other things) this blocks all SRV requests,
# so don't use it if you use eg Kerberos, SIP, XMMP or Google-talk.
# This option only affects forwarding, SRV records originating for
# dnsmasq (via srv-host= lines) are not suppressed by it.
#filterwin2k

# Change this line if you want dns to get its upstream servers from
# somewhere other that /etc/resolv.conf
#resolv-file=

# By  default,  dnsmasq  will  send queries to any of the upstream
# servers it knows about and tries to favour servers to are  known
# to  be  up.  Uncommenting this forces dnsmasq to try each query
# with  each  server  strictly  in  the  order  they   appear   in
# /etc/resolv.conf
#strict-order

# If you don't want dnsmasq to read /etc/resolv.conf or any other
# file, getting its servers from this file instead (see below), then
# uncomment this.
#no-resolv

# If you don't want dnsmasq to poll /etc/resolv.conf or other resolv
# files for changes and re-read them then uncomment this.
#no-poll

# Add other name servers here, with domain specs if they are for
# non-public domains.
#server=/localnet/192.168.0.1

# Example of routing PTR queries to nameservers: this will send all 
# address->name queries for 192.168.3/24 to nameserver 10.1.2.3
#server=/3.168.192.in-addr.arpa/10.1.2.3

# Add local-only domains here, queries in these domains are answered
# from /etc/hosts or DHCP only.
#local=/localnet/

# Add domains which you want to force to an IP address here.
# The example below send any host in doubleclick.net to a local
# webserver.
#address=/doubleclick.net/127.0.0.1

# --address (and --server) work with IPv6 addresses too.
#address=/www.thekelleys.org.uk/fe80::20d:60ff:fe36:f83

# You can control how dnsmasq talks to a server: this forces 
# queries to 10.1.2.3 to be routed via eth1
# --server=10.1.2.3@eth1

# and this sets the source (ie local) address used to talk to
# 10.1.2.3 to 192.168.1.1 port 55 (there must be a interface with that
# IP on the machine, obviously).
# --server=10.1.2.3@192.168.1.1#55

# If you want dnsmasq to change uid and gid to something other
# than the default, edit the following lines.
#user=
#group=

# If you want dnsmasq to listen for DHCP and DNS requests only on
# specified interfaces (and the loopback) give the name of the
# interface (eg eth0) here.
# Repeat the line for more than one interface.
#interface=eth1
interface=eth3
# Or you can specify which interface _not_ to listen on
#except-interface=eth0
# Or which to listen on by address (remember to include 127.0.0.1 if
# you use this.)
listen-address= 127.0.0.1
listen-address= 10.10.0.1
# If you want dnsmasq to provide only DNS service on an interface,
# configure it as shown above, and then use the following line to
# disable DHCP on it.
#no-dhcp-interface=eth0

# On systems which support it, dnsmasq binds the wildcard address,
# even when it is listening on only some interfaces. It then discards
# requests that it shouldn't reply to. This has the advantage of
# working even when interfaces come and go and change address. If you
# want dnsmasq to really bind only the interfaces it is listening on,
# uncomment this option. About the only time you may need this is when
# running another nameserver on the same machine.
#bind-interfaces

# If you don't want dnsmasq to read /etc/hosts, uncomment the
# following line.
#no-hosts
# or if you want it to read another file, as well as /etc/hosts, use
# this.
#addn-hosts=/etc/banner_add_hosts

# Set this (and domain: see below) if you want to have a domain
# automatically added to simple names in a hosts-file.
#expand-hosts

# Set the domain for dnsmasq. this is optional, but if it is set, it
# does the following things.
# 1) Allows DHCP hosts to have fully qualified domain names, as long
#     as the domain part matches this setting.
# 2) Sets the "domain" DHCP option thereby potentially setting the
#    domain of all systems configured by DHCP
# 3) Provides the domain part for "expand-hosts"
#domain=thekelleys.org.uk

# Set a different domain for a particular subnet
#domain=wireless.thekelleys.org.uk,192.168.2.0/24

# Same idea, but range rather then subnet
#domain=reserved.thekelleys.org.uk,192.68.3.100,192.168.3.200

# Uncomment this to enable the integrated DHCP server, you need
# to supply the range of addresses available for lease and optionally
# a lease time. If you have more than one network, you will need to
# repeat this for each network on which you want to supply DHCP
# service.
dhcp-range=eth3,10.10.0.10,10.10.0.150,8h

# This is an example of a DHCP range where the netmask is given. This
# is needed for networks we reach the dnsmasq DHCP server via a relay
# agent. If you don't know what a DHCP relay agent is, you probably
# don't need to worry about this.
#dhcp-range=192.168.0.50,192.168.0.150,255.255.255.0,12h

# This is an example of a DHCP range with a network-id, so that
# some DHCP options may be set only for this network.
#dhcp-range=red,192.168.0.50,192.168.0.150

# Supply parameters for specified hosts using DHCP. There are lots
# of valid alternatives, so we will give examples of each. Note that
# IP addresses DO NOT have to be in the range given above, they just
# need to be on the same network. The order of the parameters in these
# do not matter, it's permissble to give name,adddress and MAC in any order

# Always allocate the host with ethernet address 11:22:33:44:55:66
# The IP address 192.168.0.60
#dhcp-host=11:22:33:44:55:66,192.168.0.60

# Always set the name of the host with hardware address
# 11:22:33:44:55:66 to be "fred"
#dhcp-host=11:22:33:44:55:66,fred

# Always give the host with ethernet address 11:22:33:44:55:66
# the name fred and IP address 192.168.0.60 and lease time 45 minutes
#dhcp-host=11:22:33:44:55:66,fred,192.168.0.60,45m

# Give a host with ethernet address 11:22:33:44:55:66 or
# 12:34:56:78:90:12 the IP address 192.168.0.60. Dnsmasq will assume
# that these two ethernet interfaces will never be in use at the same
# time, and give the IP address to the second, even if it is already
# in use by the first. Useful for laptops with wired and wireless
# addresses.
#dhcp-host=11:22:33:44:55:66,12:34:56:78:90:12,192.168.0.60

# Give the machine which says its name is "bert" IP address
# 192.168.0.70 and an infinite lease
#dhcp-host=bert,192.168.0.70,infinite

# Always give the host with client identifier 01:02:02:04
# the IP address 192.168.0.60
#dhcp-host=id:01:02:02:04,192.168.0.60

# Always give the host with client identifier "marjorie"
# the IP address 192.168.0.60
#dhcp-host=id:marjorie,192.168.0.60

# Enable the address given for "judge" in /etc/hosts
# to be given to a machine presenting the name "judge" when
# it asks for a DHCP lease.
#dhcp-host=judge

# Never offer DHCP service to a machine whose ethernet
# address is 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,ignore

# Ignore any client-id presented by the machine with ethernet
# address 11:22:33:44:55:66. This is useful to prevent a machine
# being treated differently when running under different OS's or
# between PXE boot and OS boot.
#dhcp-host=11:22:33:44:55:66,id:*

# Send extra options which are tagged as "red" to
# the machine with ethernet address 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,net:red

# Send extra options which are tagged as "red" to
# any machine with ethernet address starting 11:22:33:
#dhcp-host=11:22:33:*:*:*,net:red

# Ignore any clients which are specified in dhcp-host lines
# or /etc/ethers. Equivalent to ISC "deny unkown-clients".
# This relies on the special "known" tag which is set when 
# a host is matched.
#dhcp-ignore=#known

# Send extra options which are tagged as "red" to any machine whose
# DHCP vendorclass string includes the substring "Linux"
#dhcp-vendorclass=red,Linux

# Send extra options which are tagged as "red" to any machine one
# of whose DHCP userclass strings includes the substring "accounts"
#dhcp-userclass=red,accounts

# Send extra options which are tagged as "red" to any machine whose
# MAC address matches the pattern.
#dhcp-mac=red,00:60:8C:*:*:*

# If this line is uncommented, dnsmasq will read /etc/ethers and act
# on the ethernet-address/IP pairs found there just as if they had
# been given as --dhcp-host options. Useful if you keep
# MAC-address/host mappings there for other purposes.
#read-ethers

# Send options to hosts which ask for a DHCP lease.
# See RFC 2132 for details of available options.
# Common options can be given to dnsmasq by name: 
# run "dnsmasq --help dhcp" to get a list.
# Note that all the common settings, such as netmask and
# broadcast address, DNS server and default route, are given
# sane defaults by dnsmasq. You very likely will not need 
# any dhcp-options. If you use Windows clients and Samba, there
# are some options which are recommended, they are detailed at the
# end of this section.

# Override the default route supplied by dnsmasq, which assumes the
# router is the same machine as the one running dnsmasq.
# dhcp-option=3,1.2.3.4

# Do the same thing, but using the option name
# dhcp-option=option:router,1.2.3.4

# Override the default route supplied by dnsmasq and send no default
# route at all. Note that this only works for the options sent by
# default (1, 3, 6, 12, 28) the same line will send a zero-length option 
# for all other option numbers.
# dhcp-option=3

# Set the NTP time server addresses to 192.168.0.4 and 10.10.0.5
#dhcp-option=option:ntp-server,192.168.0.4,10.10.0.5

# Set the NTP time server address to be the same machine as
# is running dnsmasq
#dhcp-option=42,0.0.0.0

# Set the NIS domain name to "welly"
#dhcp-option=40,welly

# Set the default time-to-live to 50
#dhcp-option=23,50

# Set the "all subnets are local" flag
#dhcp-option=27,1

# Send the etherboot magic flag and then etherboot options (a string).
#dhcp-option=128,e4:45:74:68:00:00
#dhcp-option=129,NIC=eepro100

# Specify an option which will only be sent to the "red" network
# (see dhcp-range for the declaration of the "red" network)
# Note that the net: part must precede the option: part.
#dhcp-option = net:red, option:ntp-server, 192.168.1.1

# The following DHCP options set up dnsmasq in the same way as is specified
# for the ISC dhcpcd in
# [http://www.samba.org/samba/ftp/docs/textdocs/DHCP-Server-Configuration.txt](http://www.samba.org/samba/ftp/docs/textdocs/DHCP-Server-Configuration.txt)
# adapted for a typical dnsmasq installation where the host running
# dnsmasq is also the host running samba.
# you may want to uncomment some or all of them if you use 
# Windows clients and Samba.
#dhcp-option=19,0           # option ip-forwarding off
#dhcp-option=44,0.0.0.0     # set netbios-over-TCP/IP nameserver(s) aka WINS #server(s)
#dhcp-option=45,0.0.0.0     # netbios datagram distribution server
#dhcp-option=46,8           # netbios node type

# Send RFC-3397 DNS domain search DHCP option. WARNING: Your DHCP client
# probably doesn't support this......
#dhcp-option=option:domain-search,eng.apple.com,marketing.apple.com

# Send RFC-3442 classless static routes (note the netmask encoding)
#dhcp-option=121,192.168.1.0/24,1.2.3.4,10.0.0.0/8,5.6.7.8

# Send vendor-class specific options encapsulated in DHCP option 43. 
# The meaning of the options is defined by the vendor-class so
# options are sent only when the client supplied vendor class
# matches the class given here. (A substring match is OK, so "MSFT" 
# matches "MSFT" and "MSFT 5.0"). This example sets the
# mtftp address to 0.0.0.0 for PXEClients.
#dhcp-option=vendor:PXEClient,1,0.0.0.0

# Send microsoft-specific option to tell windows to release the DHCP lease
# when it shuts down. Note the "i" flag, to tell dnsmasq to send the
# value as a four-byte integer - that's what microsoft wants. See
# [http://technet2.microsoft.com/WindowsServer/en/library/a70f1bb7-d2d4-49f0-96d6-4b7414ecfaae1033.mspx?mfr=true](http://technet2.microsoft.com/WindowsServer/en/library/a70f1bb7-d2d4-49f0-96d6-4b7414ecfaae1033.mspx?mfr=true)
#dhcp-option=vendor:MSFT,2,1i

# Send the Encapsulated-vendor-class ID needed by some configurations of
# Etherboot to allow is to recognise the DHCP server.
#dhcp-option=vendor:Etherboot,60,"Etherboot"

# Send options to PXELinux. Note that we need to send the options even
# though they don't appear in the parameter request list, so we need
# to use dhcp-option-force here. 
# See [http://syslinux.zytor.com/pxe.php#special](http://syslinux.zytor.com/pxe.php#special) for details.
# Magic number - needed before anything else is recognised
#dhcp-option-force=208,f1:00:74:7e
# Configuration file name
#dhcp-option-force=209,configs/common
# Path prefix
#dhcp-option-force=210,/tftpboot/pxelinux/files/
# Reboot time. (Note 'i' to send 32-bit value)
#dhcp-option-force=211,30i

# Set the boot filename for netboot/PXE. You will only need 
# this is you want to boot machines over the network and you will need
# a TFTP server; either dnsmasq's built in TFTP server or an
# external one. (See below for how to enable the TFTP server.)
#dhcp-boot=pxelinux.0

# Boot for Etherboot gPXE. The idea is to send two different
# filenames, the first loads gPXE, and the second tells gPXE what to
# load. The dhcp-match sets the gpxe tag for requests from gPXE.
#dhcp-match=gpxe,175 # gPXE sends a 175 option.
#dhcp-boot=net:#gpxe,undionly.kpxe
#dhcp-boot=mybootimage
 
# Encapsulated options for Etherboot gPXE. All the options are
# encapsulated within option 175
#dhcp-option=encap:175, 1, 5b         # priority code
#dhcp-option=encap:175, 176, 1b       # no-proxydhcp 
#dhcp-option=encap:175, 177, string   # bus-id 
#dhcp-option=encap:175, 189, 1b       # BIOS drive code
#dhcp-option=encap:175, 190, user     # iSCSI username
#dhcp-option=encap:175, 191, pass     # iSCSI password

# Test for the architecture of a netboot client. PXE clients are
# supposed to send their architecture as option 93. (See RFC 4578)
#dhcp-match=peecees, option:client-arch, 0 #x86-32
#dhcp-match=itanics, option:client-arch, 2 #IA64
#dhcp-match=hammers, option:client-arch, 6 #x86-64
#dhcp-match=mactels, option:client-arch, 7 #EFI x86-64 

# Do real PXE, rather than just booting a single file, this is an
# alternative to dhcp-boot.
#pxe-prompt="What system shall I netboot?"
# or with timeout before first available action is taken:
#pxe-prompt="Press F8 for menu.", 60

# Available boot services. for PXE.
#pxe-service=x86PC, "Boot from local disk"

# Loads <tftp-root>/pxelinux.0 from dnsmasq TFTP server.
#pxe-service=x86PC, "Install Linux", pxelinux 

# Loads <tftp-root>/pxelinux.0 from TFTP server at 1.2.3.4.
# Beware this fails on old PXE ROMS.
#pxe-service=x86PC, "Install Linux", pxelinux, 1.2.3.4 

# Use bootserver on network, found my multicast or broadcast.
#pxe-service=x86PC, "Install windows from RIS server", 1

# Use bootserver at a known IP address.
#pxe-service=x86PC, "Install windows from RIS server", 1, 1.2.3.4

# If you have multicast-FTP available,
# information for that can be passed in a similar way using options 1
# to 5. See page 19 of
# [http://download.intel.com/design/archives/wfm/downloads/pxespec.pdf](http://download.intel.com/design/archives/wfm/downloads/pxespec.pdf)  

  
# Enable dnsmasq's built-in TFTP server
#enable-tftp

# Set the root directory for files availble via FTP.
#tftp-root=/var/ftpd

# Make the TFTP server more secure: with this set, only files owned by
# the user dnsmasq is running as will be send over the net.
#tftp-secure

# This option stops dnsmasq from negotiating a larger blocksize for TFTP 
# transfers. It will slow things down, but may rescue some broken TFTP
# clients.
#tftp-no-blocksize

# Set the boot file name only when the "red" tag is set.
#dhcp-boot=net:red,pxelinux.red-net

# An example of dhcp-boot with an external TFTP server: the name and IP
# address of the server are given after the filename.
# Can fail with old PXE ROMS. Overridden by --pxe-service.
#dhcp-boot=/var/ftpd/pxelinux.0,boothost,192.168.0.3

# Set the limit on DHCP leases, the default is 150
#dhcp-lease-max=150

# The DHCP server needs somewhere on disk to keep its lease database.
# This defaults to a sane location, but if you want to change it, use
# the line below.
#dhcp-leasefile=/var/lib/misc/dnsmasq.leases

# Set the DHCP server to authoritative mode. In this mode it will barge in
# and take over the lease for any client which broadcasts on the network,
# whether it has a record of the lease or not. This avoids long timeouts
# when a machine wakes up on a new network. DO NOT enable this if there's
# the slighest chance that you might end up accidentally configuring a DHCP
# server for your campus/company accidentally. The ISC server uses
# the same option, and this URL provides more information:
# [http://www.isc.org/index.pl?/sw/dhcp/authoritative.php](http://www.isc.org/index.pl?/sw/dhcp/authoritative.php)
#dhcp-authoritative

# Run an executable when a DHCP lease is created or destroyed.
# The arguments sent to the script are "add" or "del", 
# then the MAC address, the IP address and finally the hostname
# if there is one. 
#dhcp-script=/bin/echo

# Set the cachesize here.
cache-size=10000

# If you want to disable negative caching, uncomment this.
#no-negcache

# Normally responses which come form /etc/hosts and the DHCP lease
# file have Time-To-Live set as zero, which conventionally means
# do not cache further. If you are happy to trade lower load on the
# server for potentially stale date, you can set a time-to-live (in
# seconds) here.
#local-ttl=

# If you want dnsmasq to detect attempts by Verisign to send queries
# to unregistered .com and .net hosts to its sitefinder service and
# have dnsmasq instead return the correct NXDOMAIN response, uncomment
# this line. You can add similar lines to do the same for other
# registries which have implemented wildcard A records.
#bogus-nxdomain=64.94.110.11

# If you want to fix up DNS results from upstream servers, use the
# alias option. This only works for IPv4.
# This alias makes a result of 1.2.3.4 appear as 5.6.7.8
#alias=1.2.3.4,5.6.7.8
# and this maps 1.2.3.x to 5.6.7.x
#alias=1.2.3.0,5.6.7.0,255.255.255.0
# and this maps 192.168.0.10->192.168.0.40 to 10.0.0.10->10.0.0.40
#alias=192.168.0.10-192.168.0.40,10.0.0.0,255.255.255.0

# Change these lines if you want dnsmasq to serve MX records.

# Return an MX record named "maildomain.com" with target
# servermachine.com and preference 50
#mx-host=maildomain.com,servermachine.com,50

# Set the default target for MX records created using the localmx option.
#mx-target=servermachine.com

# Return an MX record pointing to the mx-target for all local
# machines.
#localmx

# Return an MX record pointing to itself for all local machines.
#selfmx

# Change the following lines if you want dnsmasq to serve SRV
# records.  These are useful if you want to serve ldap requests for
# Active Directory and other windows-originated DNS requests.
# See RFC 2782.
# You may add multiple srv-host lines.
# The fields are <name>,<target>,<port>,<priority>,<weight>
# If the domain part if missing from the name (so that is just has the
# service and protocol sections) then the domain given by the domain=
# config option is used. (Note that expand-hosts does not need to be
# set for this to work.)

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 289
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 289 (using domain=)
#domain=example.com
#srv-host=_ldap._tcp,ldapserver.example.com,389

# Two SRV records for LDAP, each with different priorities
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,1
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,2

# A SRV record indicating that there is no LDAP server for the domain
# example.com
#srv-host=_ldap._tcp.example.com

# The following line shows how to make dnsmasq serve an arbitrary PTR
# record. This is useful for DNS-SD. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for PTR records.)
#ptr-record=_http._tcp.dns-sd-services,"New Employee Page._http._tcp.dns-sd-services"

# Change the following lines to enable dnsmasq to serve TXT records.
# These are used for things like SPF and zeroconf. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for TXT records.)

#Example SPF.
#txt-record=example.com,"v=spf1 a -all"

#Example zeroconf
#txt-record=_http._tcp.example.com,name=value,paper=A4

# Provide an alias for a "local" DNS name. Note that this _only_ works
# for targets which are names from DHCP or /etc/hosts. Give host
# "bert" another name, bertrand
#cname=bertand,bert

# For debugging purposes, log each DNS query as it passes through
# dnsmasq.
#log-queries

# Log lots of extra information about DHCP transactions.
#log-dhcp

# Include a another lot of configuration options.
#conf-file=/etc/dnsmasq.more.conf
#conf-dir=/etc/dnsmasq.d

---

### Post by darkod on 2013-07-04
> **hawaiiman said:**
> yes to 10.10.0.1  yes to 127.0.0.1  no to eth0 or past that

There is no point to try pinging 127.0.0.1 from a client, it will ping its own machine.
So, you can ping the server, but not the internet, for example 8.8.8.8?
It looks like the server is not forwarding between its interfaces any more.

Also can you post the running services on the server?
```
sudo netstat -plunt
```

---

### Post by hawaiiman on 2013-07-04
```
netstat -plunt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      1201/dnsmasq    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1955/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1439/cupsd      
tcp        0      0 0.0.0.0:3128            0.0.0.0:*               LISTEN      1417/(squid)    
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1347/master     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      927/smbd        
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      927/smbd        
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1500/apache2    
tcp6       0      0 :::53                   :::*                    LISTEN      1201/dnsmasq    
tcp6       0      0 :::22                   :::*                    LISTEN      1955/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      1439/cupsd      
tcp6       0      0 :::5900                 :::*                    LISTEN      2500/vino-server
udp        0      0 0.0.0.0:53              0.0.0.0:*                           1201/dnsmasq    
udp        0      0 0.0.0.0:3130            0.0.0.0:*                           1417/(squid)    
udp        0      0 0.0.0.0:63036           0.0.0.0:*                           1201/dnsmasq    
udp        0      0 0.0.0.0:67              0.0.0.0:*                           1201/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1169/dhclient   
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1636/dhclient3  
udp        0      0 0.0.0.0:46924           0.0.0.0:*                           1201/dnsmasq    
udp        0      0 10.10.0.1:123           0.0.0.0:*                           2170/ntpd       
udp        0      0 192.168.1.5:123         0.0.0.0:*                           2170/ntpd       
udp        0      0 127.0.0.1:123           0.0.0.0:*                           2170/ntpd       
udp        0      0 0.0.0.0:123             0.0.0.0:*                           2170/ntpd       
udp        0      0 0.0.0.0:17927           0.0.0.0:*                           1201/dnsmasq    
udp        0      0 10.10.0.1:137           0.0.0.0:*                           1753/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1753/nmbd       
udp        0      0 10.10.0.1:138           0.0.0.0:*                           1753/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1753/nmbd       
udp        0      0 0.0.0.0:38417           0.0.0.0:*                           1417/(squid)    
udp6       0      0 :::53                   :::*                                1201/dnsmasq    
udp6       0      0 fe80::4687:fcff:fec:123 :::*                                2170/ntpd       
udp6       0      0 fe80::a2f3:c1ff:fe1:123 :::*                                2170/ntpd       
udp6       0      0 ::1:123                 :::*                                2170/ntpd       
udp6       0      0 :::123                  :::*                                2170/ntpd
```

---

### Post by hawaiiman on 2013-07-04
just to try, I disabled and purged ufw. too much stuff happening.

---

### Post by hawaiiman on 2013-07-04
[B]IPTABLES  -I INPUT -i LAN_IFACE -p udp --dport 67:68 --sport \      67:68 -j ACCEPT

would this get dhcp working?
[/B]

---

### Post by hawaiiman on 2013-07-05
I made the dnsmasq setting less specific, after reading that by default, dnsmasq is "open" and naming something makes it more closed. Took it to school, and it works fine again. Thanks all for your kindness in helping me.

---

### Post by darkod on 2013-07-05
No problem, glad you got it sorted out at the end. Yeah, it's often best to keep things simple, as long as they do what you need. Linux is great with flexibility, but that doesn't mean we should touch everything. :)

---

