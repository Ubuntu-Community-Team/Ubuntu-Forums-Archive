---
title: "Cannot get ethernet working"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by higgins on 2009-07-19
Hi

I cannot get ethernet to connect via DHCP or manually after installing Ubuntu 9.04 using my network information:

Default Gateway - 192.168.1.254
Net Mask - 255.255.255.0
DNS - 192.168.1.254
IP Address - 192.168.1.5

I tried using the Live CD also and that does not work either.

Searching the forums I have gathered the following information from my equipment:

**Active Network Connection **

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121602&stc=1&d=1247990919[/IMG]

**ifconfig OUTPUT **

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121603&stc=1&d=1247990922[/IMG]

**lspci output **

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121604&stc=1&d=1247990922[/IMG]

Any ideas on how I get this working?

---

### Post by aesis05401 on 2009-07-19
How did you input the address information shown in your screenshots?

---

### Post by higgins on 2009-07-19
> How did you input the address information shown in your screenshots?

I changed the connection type to manual and entered the information via the user interface while booted into the live  CD

---

### Post by Kraut~salat on 2009-07-19
what exactly isn't working? You cannot connect to the Internet net thru a router, you cannot connect to the router, you don't get name resolution...?

please post the output of "netstat -rn"

Can you ping your gateway 192.168.1.254?

---

### Post by aesis05401 on 2009-07-19
> **higgins said:**
> I changed the connection type to manual and entered the information via the user interface while booted into the live  CD

K, provided the address you assigned is within your DHCP server parameters, you should be able open a terminal and type in :
```

sudo dhclient

```

This will cause your machine to broadcast a dhcp request with the IP address you assigned.  

I do not use the gui to configure my network, but it sounds like you are not actually getting a lease (contacting the dhcp server), or there is something wrong with your address numbers.

Does this help?

---

### Post by higgins on 2009-07-19
> what exactly isn't working?

Internet is not working

> You cannot connect to the Internet net thru a router, you cannot connect to the router, you don't get name resolution...?

I cannot get to the internet via my router 192.168.1.254

> please post the output of "netstat -rn"

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121611&stc=1&d=1247996080[/IMG]

>  Can you ping your gateway 192.168.1.254?

No

> sudo dhclient

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121612&stc=1&d=1247996082[/IMG]

---

### Post by Kraut~salat on 2009-07-19
well there we have it. Your default rouet is incorrect.

See the output of netstat -rn. The line with "Destination 0.0.0.0" also says "Gateway 0.0.0.0". That is incorrect, it should be 192.168.1.254 there.

Type: 
route del default
route add default gw 192.168.1.254
netstat -rn

that should fix it. Also make sure you have
nameserver 192.168.1.254
in your /etc/resolv.conf


edit: just saw that your DHCP doesn't work at all (No DHCPOFFERS received). That will reset your IP adress to some random number in the 169.xxxxx region. You have to set it back to the 192.168.1.0 net manually.

---

### Post by higgins on 2009-07-19
> route del default
route add default gw 192.168.1.254
netstat -rn

After doing that I can now ping the gateway however I still cannot get on the internet. Attached is the output of netstat -rn below:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121617&stc=1&d=1248000072[/IMG]

---

### Post by Kraut~salat on 2009-07-19
What does "cannot connect" mean? You cannot resolve a server name via DNS or your requests are not forwarded by the router? Does 
ping 209.85.129.104
work?

What happens if you try 
ping [www.google.com](www.google.com)
? Can it resolve the host name?
Is your router working? I get the impression it is not, since your DHCP doesn't work at all. Then probably your routers DNS service doesn't work as well and it probably doesn't forward inet requests.

Also post the output of
cat /etc/resolv.conf

---

### Post by higgins on 2009-07-19
> What does "cannot connect" mean? 

My browser does not display any pages

> You cannot resolve a server name via DNS or your requests are not forwarded by the router? 

Names and IP addresses are not resolving

> Does ping 209.85.129.104 work?

No it says:

PING 209.85.129.104 (209.85.129.104) 56(84) bytes of data.
From 192.168.1.5 icmp_seq=2 Destination Host Unreachable
From 192.168.1.5 icmp_seq=3 Destination Host Unreachable

> What happens if you try ping [www.google.com](www.google.com) ? Can it resolve the host name?

No, it says:

ping: unkown host [www.google.com](www.google.com)

> Is your router working? I get the impression it is not, since your DHCP doesn't work at all. Then probably your routers DNS service doesn't work as well and it probably doesn't forward inet requests.


Yes router is working, I have a windows box that was assigned an IP via DHCP from it.

> Also post the output of cat /etc/resolv.conf

#Generated by NetworkManager
nameserver 192.168.1.254

---

### Post by Kraut~salat on 2009-07-19
the "destination host unreachable" message tells me that your router is not forwarding your traffic (assuming your default route is still set to the router's ip adress). This could be, because you set your own ip manually. Maybe the router only accepts requests from hosts it assigned ips via DHCP. I can't help you anymore at this point. If your default route is correct I would look at the router for the problem. I wonder why it doesn't assign an ip to your PC via DHCP. Once you fixed that you probably fixed everything

---

### Post by higgins on 2009-07-19
I checked my router and Mac address filtering was enabled. This prevented it from working...

I thought I only had this on for wifi but it seems its enabled for ethernet too.

I added the mac addresses of my two NICs and its working

---

