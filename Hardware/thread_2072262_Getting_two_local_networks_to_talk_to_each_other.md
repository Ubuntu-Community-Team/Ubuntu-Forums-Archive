---
title: "Getting two local networks to talk to each other"
date: 2012-10-17
forum: Hardware
---

### Post by Leo Simon on 2012-10-17
Having run out of lan ports on my router, which uses 192.168 addresses, I'm now using the LAN ports on my modem as well, which uses 10.1.10 addresses.   My printer is installed as 192.168.1.202 but I can't access it from a wired connection with address beginning with 10.1.10.     I've read posts on the web relating to this, but am looking a 'for dummies' answer

Could anybody offer a simple solution please

---

### Post by PowerBarry43 on 2012-10-17
Hi 

you could "add" more ports to your router by buying a cheap miniswitch for example

[http://www.ebuyer.com/132456-tenda-5-port-10-100-switch-s105](http://www.ebuyer.com/132456-tenda-5-port-10-100-switch-s105)

which you could connect to the back of your router and so you can start connecting your devices to the switch.

from what you've told me i think the problem is that you have NAT on your router which means that all addresses in the 192.168 range are squeezed into one 10.1.10 address. you can work around this by forwarding ports in the configuration pages of the router or by adding a switch behind your router, increasing the number of ports available.

hope this helps!

Barry

---

### Post by TheFu on 2012-10-17
Most home routers easily support 255 devices on the same network based on the default netmask, 255.255.255.0 (or /24). If you need more ports, any cheap $20 switch can be added to any of the router ports to add more ports for devices on the same network.  When you have more devices, add another switch to a different router port.  

They sell 24-port switches relatively cheap, but 5 and 8 port versions for $20 or less work well too.

Anyway, with a 4 port router and 4 24-port switches, you can support ... 96 directly attached devices on the same /24 subnet.  If your router supports dd-wrt or some other aftermarket firmware, you can control the subnet mask and probably support 2048 devices and multiple subnets using vlans or just larger subnet masks.

If you are just needing a few more devices, a 5-port switch is more than sufficient for most homes.  I have (2) 8-port switches myself.  Best of all, it is just another connection and no change to the computer settings is needed at all.

---

### Post by Leo Simon on 2012-10-17
Thanks, I've ordered a five-port extender and will see how it goes!

Leo

---

### Post by TheFu on 2012-10-17
> **Leo Simon said:**
> Thanks, I've ordered a five-port extender and will see how it goes!

Leo

I hope that is a **5-port GigE Switch,** since I've never heard of an "extender" for networking.  That might not be what you really want if it is a "KVM extender." Perhaps it is a UK-English thing vs US-English thing?

Also, I hope you ordered a GigE switch even if your router isn't GigE capable.  When all the devices are on the same subnet and connected to a GigE switch, all the packets can move quicker.  It is especially helpful if the network cards involved are GigE too, then you go from 11MB/s to 70+MB/s file transfers.  The difference in performance helps in other ways too, even if your ISP connection is only 1.5Mbps/256Kbps up.

---

### Post by Scott Goodgame on 2012-10-18
Couldn't you have just changed your router to 10.x.x.x being, say one ip higher than the modem? Just let the router act as a switch since that is what you are doing...

---

