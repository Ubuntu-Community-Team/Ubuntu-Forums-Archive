---
title: "Ubuntu Server from a router"
date: 2022-10-20
forum: Hardware
---

### Post by graviton75 on 2022-10-20
Hello Everyone! I'd like to initiate a brainstorming here, if you find the topic interesting. How could I turn a quite powerful wifi router (Linksys WRT32X) into an all-pupose linux box? It's an ARM-based device (if I'm not mistaken Cortex A9, dual core) and eg. Ubuntu Server has an ARM edition. So, what would you guys do, software and hardware-wise? Ideas? Thanks!

---

### Post by Tadaen_Sylvermane on 2022-10-20
Don't think you can. While the processor and memory may be enough the raw storage to fit Ubuntu isn't there. Maybe you could increase the storage or run from an attached usb drive? Not sure how that would work.

You can however easily take a low spec machine with a normal ssd / hard drive and use it as both a router and a server. I've done that with Debian. Had docker running a transparent squid proxy. Dnsmasq provided dhcp and dns. Iptables provided the routing part of it. Of course 2 nics are required.

A script I built up for routing on boot for reference.

[https://gitlab.com/jmgibson1981/homescripts/-/tree/master/router](https://gitlab.com/jmgibson1981/homescripts/-/tree/master/router)

---

### Post by mIk3_08 on 2022-10-21
> **graviton75 said:**
> Hello Everyone! I'd like to initiate a  brainstorming here, if you find the topic interesting. How could I turn a  quite powerful wifi router (Linksys WRT32X) into an all-pupose linux  box? It's an ARM-based device (if I'm not mistaken Cortex A9, dual core)  and eg. Ubuntu Server has an ARM edition. So, what would you guys do,  software and hardware-wise? Ideas? Thanks! I don't know what you  mean by "all-pupose linux box" If you want to upgrade your router  firmware you can do it with "Linux based alternative OpenSource firmware  for routers" Its pretty powerful and I have done it my self. And I was  very amaze with the features that I get from the open source firmware.  Just check out [here]("https://dd-wrt.com/"). Regards and cheers.

---

