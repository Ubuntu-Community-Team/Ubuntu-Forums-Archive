---
title: "Network Gateway"
date: 2008-11-18
forum: General Help
---

### Post by months on 2008-11-18
I think that this is a real noob question but, how do I determine my Network Gateway?

---

### Post by DGortze380 on 2008-11-18
> **months said:**
> I think that this is a real noob question but, how do I determine my Network Gateway?

What are you trying to do? The gateway is typically the internal address of your router.

---

### Post by 420shaggy on 2008-11-18
If you go into a terminal and enter ifconfig ( -help to see more options ) you can get lots of info on your network devices and ips.  

  If you just want to know the network gateway ip address, typically it would be 192.168.1.1

---

### Post by DGortze380 on 2008-11-18
> **420shaggy said:**
> If you go into a terminal and enter ifconfig ( -help to see more options ) you can get lots of info on your network devices and ips.  

  If you just want to know the network gateway ip address, typically it would be 192.168.1.1

Please don't give random advice. You do not now what his gateway is, it depends on the router. For all we know right now it could be 10.0.1.1 ... or 10.0.0.1 or ... 172.16.0.1 or ... 192.168.0.1 etc. etc. etc.

As for ifconfig, he is welcome to try it. But we don't know why he needs the information. ifconfig may very well give him the wrong address depending what he is trying to configure.

---

### Post by months on 2008-11-18
*What are you trying to do? *

I inherited a several year old Dell from my parents a few weeks ago.  I had never tried linux before (I'm a Mac person) so I thought that it would be fun to try (I now have dual-booted my new Macbook with Ubuntu as well).  After reading more about linux these last few weeks I've decided to try to make the Dell into a server to store primarily music that I can access from within my college's network.  I've been thinking that I will try to use the Amahi/Fedora 9 setup as it appears to be easy and user friendly.  Setting up Amahi requires the network gateway.

Thanks for the help

---

