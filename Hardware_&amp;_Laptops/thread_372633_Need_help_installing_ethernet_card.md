---
title: "Need help installing ethernet card"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by Sureshot324 on 2007-02-28
I have an old Dell pentium 3 that I installed Xubuntu on.  It has no integrated ethernet so I was using an old 10mbit pci ethernet card until it died.  I bought a new 10/100 ethernet card but I can't get it working.

There is no eth0 file anywhere in /dev/. When I run lspci, it shows up as:

00:0f.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller

What do I have to do to get this card running?  Shouldn't Xubuntu already have drivers for this stored on the hard drive as I'm sure Windows would?  If not, can I get them from the CD because without ethernet I can't get on the internet to download the drivers, unless I download them with my other computer and transfer them with a USB stick.

---

### Post by Sureshot324 on 2007-02-28
I did some googling and I'm pretty sure the driver module for my ethernet card is natsemi.

I can modprobe natsemi and it seems to load the module fine (it's there when I go lsmod).  I ran ifconfig and there is an eth1 but no eth0, and it doesn't show an IP address for eth1.  I'm not even sure eth1 refers to my ethernet card.

I tried ifdown eth1 and then ifup eth1.  I got a bunch of messages like this:

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
.....
No DHCPOFFERS received
No working leases in persistent database - sleeping.

Firefox still won't connect so I know I don't have a connection. I don't know too much about linux and I'm unsure what to do next.  I don't really want to reinstall Xubuntu.  Anyone have any ideas?

---

### Post by Sureshot324 on 2007-03-01
Fixed it by moving to a different pci slot.

---

