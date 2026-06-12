---
title: "problem with forcedeth driver for nvidia nforce2 chipset nic (ubuntu 7.10)"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by simons101 on 2007-10-31
problem with forcedeth driver for nvidia nforce2 chipset nic in ubuntu 7.10

thought it was the problem of ipv6/dns errors etc...  but after changing all the  alias/conf/dns/etc  fixes and it still didn't work..  i looked in the log file (should have looked there first ,  i'm new to this )

example logs 
```
Oct 31 13:10:31 hellsdata kernel: [ 3951.440236] eth0: link down. 
Oct 31 13:10:32 hellsdata kernel: [ 3953.051216] eth0: link up. 
Oct 31 13:10:38 hellsdata kernel: [ 3958.262030] eth0: link down. 
Oct 31 13:10:39 hellsdata kernel: [ 3959.959568] eth0: link up. 
Oct 31 13:10:40 hellsdata kernel: [ 3960.607090] eth0: link down. 
Oct 31 13:10:42 hellsdata kernel: [ 3962.262066] eth0: link up. 
Oct 31 13:10:57 hellsdata kernel: [ 3977.824129] eth0: link down. 
Oct 31 13:10:59 hellsdata kernel: [ 3979.480522] eth0: link up. 
Oct 31 13:11:02 hellsdata kernel: [ 3982.854195] eth0: link down. 
Oct 31 13:11:04 hellsdata kernel: [ 3984.504888] eth0: link up. 
Oct 31 13:11:05 hellsdata kernel: [ 3985.970855] eth0: link down. 
Oct 31 13:11:07 hellsdata kernel: [ 3987.540124] eth0: link up.
``` 

as u can see eth0 is up and down like a yoyo ....

lspci
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1) 

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:30:1B:B0:C6:A8  
          inet addr:192.168.1.42  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::230:1bff:feb0:c6a8/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:256 (256.0 b)  TX bytes:412 (412.0 b) 
          Interrupt:11 Base address:0x8000 

any help or advice 

thx in advance    :confused:

---

### Post by simons101 on 2007-10-31
oh  ...  my system is  an xpc shuttle  ... help  (sn45)

---

### Post by simons101 on 2007-10-31
bump :(

---

### Post by insanity2k7 on 2007-11-05
I have this hardware but have a different problem...  Not meaning to steal your thread, only thinking the resolution for both problems may be the same.

I have the same hardware and everything is working fine.  My issue is that my network performance is less than perfect.  Everything does work, just not as fast as when running Windows (sorry) on the same hardware.  I was thinking that loading up the driver for my hardware as opposed to running the "forcedeth" driver may yield better results.  Problem is I don't know how to do to that.  Anyone?

---

