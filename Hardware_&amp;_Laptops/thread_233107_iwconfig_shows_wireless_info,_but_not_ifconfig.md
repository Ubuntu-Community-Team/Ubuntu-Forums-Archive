---
title: "iwconfig shows wireless info, but not ifconfig"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by bingwalker on 2006-08-09
I have ndiswrapper installed and the windows drivers "wrapped" properly.  iwconfig shows good information, but ifconfig doesn't show my wireless info (eth1).  I have the MAC address for the wireless hardware.  Isn't there a command that I can use to add the MAC address and eth1 to the list of network devices?  I remember doing it once but I can't remember now.  And, could that even help me get on the wireless network?

---

### Post by ciscosurfer on 2006-08-09
Try:```
ifconfig -a
```

---

### Post by bingwalker on 2006-08-09
I get:

```
eth0      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:45
          inet addr:192.168.0.114  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe2f:6c45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4933 (4.8 KiB)  TX bytes:3440 (3.3 KiB)
          Interrupt:209 Base address:0x1800

eth1      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:09
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by benjaminwr on 2006-08-09
Hi

To my uderstanding... Im quite new to this but iwconfig is used to set wireless settings (essid key channel) for devices while ifconfig is used to set IP network parameters (IP address netmask etc.) not all devices need wireless parameters so I think this is why ifconfig doesn't have the ability to set them (or show them). iwconfig is what u use in adtition to ifconfig to get your wireless running.

Hope I have been of some help

Ben

---

### Post by ciscosurfer on 2006-08-09
I agree with the previous poster as to the distinction between ifconfig and iwconfig. Sorry #-oI misread your first post.  Maybe this link will help (scroll to the linux section).  Also, ```
man ifconfig
``` or ```
man iwconfig
``` might help you.

And while [this page]("http://www.cyberciti.biz/tips/linux-install-and-configure-dlink-dwl-g-520-wireless-lan-pci-card.html") is not necessarily the card you are working with, it might help.

Here's another on [configuring MAC addresses]("http://www.answers.com/topic/mac-address")

Finally, and this one's a biggie, the [FreeBSD section on Wireless Networking]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/network-wireless.html").  

I hope these help.  I really don't mess with wireless all that much.

---

