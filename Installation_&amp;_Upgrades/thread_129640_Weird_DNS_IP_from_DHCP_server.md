---
title: "Weird DNS IP from DHCP server"
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by bushtor on 2006-02-14
Hi,

I have just installed ubuntu 5.10 in a two NIC computer and had it up and running in minutes ;-)

I added the DHCP server package and configured it according to the help doc (Ubuntu FAQ Guide / Networking / DHCP):

subnet 192.168.33.0 netmask 255.255.255.0 {
range 192.168.33.50 192.168.33.250;
option domain-name-servers <my_isp_primary_dns>, <my_isp_secondary_dns>;
option domain-name "somedomain.local";
option routers 192.168.33.10;
option broadcast-address 192.168.33.255;
default-lease-time 3600;
max-lease-time 7200;
}

eth0 is connected to ADSL modem DHCP client.
eth1 is connected to local LAN, IP 192.168.33.10 and DHCP server running.

Connected client computers receive ip and gateway address as expected but they display 192.168.33.43 as DNS address.  How come?  I haven't used this particular address in any config file.  How can I have my DHCP server giveout <my_isp_primary_dns> as DNS server address?

In addition, two questions about the DHCP config above:

Is setting 'option domain-name "<domain name>";' important?  This is not a domain controller;-)

I set the 'option routers 192.168.33.10;' to the eth1 address as I assume that traffic is routed from eth0 to eth1.  Is this correct?

Thanks for comments on what can be wrong here.

regards

tor

---

### Post by joft on 2006-02-14
> **bushtor]
Connected client computers receive ip and gateway address as expected but they display 192.168.33.43 as DNS address.  How come?  I haven't used this particular address in any config file.  How can I have my DHCP server giveout <my_isp_primary_dns> as DNS server address?
[/QUOTE]

That's really strange. Do you use .43 in your local network? You don't have another DHCP server on your local network, right?

[QUOTE=bushtor]
In addition, two questions about the DHCP config above:

Is setting 'option domain-name "<domain name>" said:**
> 

It's an "option", so I think it's "optional" - AFAIK.

[QUOTE=bushtor]
I set the 'option routers 192.168.33.10;' to the eth1 address as I assume that traffic is routed from eth0 to eth1.  Is this correct?


This is correct. This will advise your clients to send any "unknown" traffic (=> Internet) to your "server" which has to route the traffic into the Internet.

---

