---
title: "Ubuntu as Router for Windows Mobile Internet Connection"
date: 2008-10-11
forum: General Help
---

### Post by bshakil on 2008-10-11
My issue is a little complicated ... 

I have an Ubuntu Server at home working as a DSL Router and DHCP Server and Shorwall Firewall.

I have the following IP Configuration.

Ubuntu Server 10.1.254.10 --->GW 10.1.254.200
Linksys DSL (Bridged) 10.1.254.200 

and all Clients are assigned DHCP ips of series 10.1.254.x

Now the Problem is .. Due to road Maintenance my dsl line is damaged and repair could take 2 weeks or more.

So i configured a Windows Mobile Internet Sharing for Ubuntu. We have 3.5 MB HSDPA Reception in our office.

Internet is working fine on Ubuntu Server. Now i want this internet to be shared on the network.

I Configured "rndis0" Interface as my Internet Zone using Webmin(Shorewall Firewall) ..

So all our DSL Rules will apply on 3g as well.

Now the Problem is ...

My rndis0 or 3g Connection has the following Configuration
rndis0 IP Address 192.168.0.102
Gateway Ip Address 192.168.0.1

They are automatically assigned and i cannot change them.

Can i share the above connection on my network of 10.1.254.x

Please provide Steps since i m a newbie in Ubuntu Routing.

Please Help... I m willing to clarify the situation as much as i can. I think this shouldnt be a big problem.

---

