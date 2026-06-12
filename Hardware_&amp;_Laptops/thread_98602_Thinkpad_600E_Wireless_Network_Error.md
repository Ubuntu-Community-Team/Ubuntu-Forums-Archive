---
title: "Thinkpad 600E Wireless Network Error"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by kbighorse on 2005-12-03
When I right-click on the network icon and select properties, my wireless network is detected correctly, but Status is Error.  Here's the ifconfig output, I don't seem to have an IP address, but now I'm stuck, thanks so much for any help!

eth0      Link encap:UNSPEC  HWaddr 00-0C-30-1F-15-27-00-19-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:78 errors:6821 dropped:0 overruns:0 frame:6821
          TX packets:3 errors:4 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:7057 (6.8 KiB)  TX bytes:1156 (1.1 KiB)
          Interrupt:3 Base address:0x100

eth1      Link encap:Ethernet  HWaddr 00:0C:30:1F:15:27
          inet6 addr: fe80::20c:30ff:fe1f:1527/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78 errors:6821 dropped:0 overruns:0 frame:6821
          TX packets:3 errors:4 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7057 (6.8 KiB)  TX bytes:1156 (1.1 KiB)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2243021 (2.1 MiB)  TX bytes:2243021 (2.1 MiB)

---

### Post by rjhale3629 on 2005-12-30
I just found your question - Maybe this will answer it. 

My niece had a thinkpad 600e - dead (she salvaged out of a junk pile) - she gave it to me and I got it back up and running. I loaded hoary on it and it worked fine - I upgraded it to breezy badger and the wireless pcmcia card wouldn't obtain an ip address. I saw several forum posts blaming dhclient - but the consensus is that it wasn't dhclient.  After much digging around on the internet I decided that it must be an irq conflict - I went in under /etc/pcmcia/config.opts and uncommented "exclude irq3" and I got the wireless card working - it now obtains an IP address...............

Hopefuly that will work

---

