---
title: "Network Problems Following nVidia Driver Install"
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by rmccarri on 2008-04-18
Hi,
I've been wanting to switch over to Ubuntu for quite some time but always end up going back to windows because a problem with my network and my nVidia video card.

After installing Ubuntu 7.10, the network works fine (I'm running MAC address directed DHCP from my Dlink router, the router assigns an IP that I designate based on the MAC address).  It grabs an IP from the wired eth0 connection.

Next, I install the restricted nVidia drivers for my video card it asks me to reboot and when I do, I am no longer able to receive an IP from the network.  ifconfig still lists my eth0 interface including the MAC hardware address.  If I try to manually restart the network, I get:

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Selecting "roaming mode" or directly setting the network connection to DHCP through the via-rhine interface does not work.

Has anyone else noticed this conflict and determined a fix?
Thanks,
Rob

---

