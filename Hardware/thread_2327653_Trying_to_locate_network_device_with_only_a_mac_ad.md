---
title: "Trying to locate network device with only a mac address as information."
date: 2016-06-13
forum: Hardware
---

### Post by JayKay3OOO on 2016-06-13
Hi Folks.

I have a device on a network that I have only been given a mac address for. Is there any linux tools that I can use to find out what its IP is?

I have tried connecting it to a local router and the laptop comes up, but not the device I want to see the IP of.

This device has a web interface, but no screen input and no other known information except and old piece of paper with its mac address on.

Since I have looked through the windows DHCP server and cannot see it when it's connected to the network I am a bit stuck. I use linux a lot so thought you guys might know of a tool or even a general way to find its IP?

The device is doing 'network stuff' since the lights are flashing and on my router it just came up blank.

Really odd.

Any help appreciated. The makers of the device have gone out of business and there does not seem to be any info about it on the web.

Note - this is a device on a windows network running DHCP and presumably connected to one of our subnets, but I thought I might be able to isolated it using a local router and my linux laptop, looking through DCHP where it 'should' be connected comes up blank as it apparently has a limited web interface.

Thanks Guys.

---

### Post by TheFu on 2016-06-14
Without the IP, you cannot connect to it.  Raw ethernet doesn´t do any good for most protocols/devices.  Only something like AoE would work - no IP.

You can scan the network using something like **nmap**, but that doesn´t mean this specific device is actually on the same subnet. For example, some devices comes with an automatic 169.x.x.x subnet if they can´t find any other.  Can also try ARP, but what good is seeing the MAC on the network without an IP? If the connection is over IP and on the same LAN (not just subnet), then that should show up in the **arp** table.

Blinking lights on the interface don´t necessarily mean it is connected to any network. It could be looking for a dhcp server and failing.

---

### Post by JayKay3OOO on 2016-06-15
Thanks for help, I'll give them a shot.

I'll keep thinking about this. Since I did not set this up I can only guess at which sub net it sits on based on which switch it's attached to.

I guess if it's static is there ever a way to know?

---

