---
title: "VPN Conflict With Wireless Network"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by ozone702 on 2007-12-13
I followed some instructions to setup VPN on 7.10 and got VPN Connections to show up in Network Manager.  Good.

I added a VPN configuration.  Good.

I tried to connect to the VPN.  Bad idea.

Now my wireless network is gone and wireless is now trying to connect to the VPN address instead of my wireless network every time!!!

I removed the VPN configuration but wireless tries to connect to the VPN address still (several re-boots later).  I keep trying to 'Connect to Other Wireless Network,' and it connects, but then disconnects and tries to connect to VPN address???

What's happening?

---

### Post by kaervos1024 on 2007-12-13
Post the output of running the following two commands in the terminal:

> ifconfig

> iwconfig

Also, what happens when you try to connect to the wireless network manually? i.e.:

> iwconfig eth0 essid "My Wireless Network" key 0123-4567-89 commit

EDIT: Obviously you'll have to change the device (eth0), the network name and the key to your own. Depending on the type of encryption your wireless has the key will take different formats. See the manual page for iwconfig for more details.

---

