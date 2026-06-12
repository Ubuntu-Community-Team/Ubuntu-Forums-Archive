---
title: "Building a Proxy Server"
date: 2013-03-18
forum: Hardware
---

### Post by haloysious on 2013-03-18
Hello All,  I'm looking to build my own (or buy off the shelf) a proxy server.  My plan is to set it up using squid and so I don't have to modify any of the clients.  Sort-of like this:

```

|--------|        |--------|        |-------|        |-----------|
| Client | <----> | Router | <----> | Squid | <----> | Modem/Int |
|--------|        |--------|        |-------|        |-----------|

```

I'm still in the learning phase, so I'm not sure if that'll even work or not.

My primary question: 
What hardware would be needed for this type of proxy?  I do not want to reduce connection speeds.
Is memory, CPU, or network cards more important?

My home network connection speed is 15/5 without plans to increase the speed.

Thanks for any help you can give in this regard.  I've found a lot of tutorials for setting up the software, but the only hardware setup I found was [http://www.anandtech.com/show/3715/family-proxy](http://www.anandtech.com/show/3715/family-proxy) which is from 2010.

---

### Post by I8NY on 2013-03-18
The hardware doesn't need to be very powerful to do a proxy. I have old Pentium 4 (~2.0GHz) machines running Samba and SSH file servers with no problem. Something over the recommended ubuntu server requirement should be fine as long as you aren't doing 100 connections with fiber internet. [Here]("http://beginlinux.com/blog/2008/11/hardware-requirements-for-squid/") are is some information on system requirements for Squid. I would say have 100MB nic or faster and at least 512MB of RAM, 768MB or more is ideal. There will be more delay because their is another step in the connection but hardware should only make 10ms difference if it isn't maxed out. Try find a free old PC, there should be enough power to do home proxy.

---

