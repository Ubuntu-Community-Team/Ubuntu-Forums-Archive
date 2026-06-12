---
title: "Internet Gateway/Router"
date: 2008-08-22
forum: General Help
---

### Post by dgcarter on 2008-08-22
I have an ubuntu box set up as my internet gateway and router with a PPPoE connection to my modem.

In the passed, I used a free windows program called Route Sentry, and DDProxy to split international and local bandwidth. Essentially, all local bandwidth would go through one ADSL account, and all Internetional bandwidth would go through the other.

Does anyone know of any software, or perhaps a method to get my ubuntu box to do this?

Thanks

---

### Post by idipous on 2008-08-22
You should try configuring it with iptables. This is not an easy task but you will be able to customize your router/firewall pretty well.

Here a couple of links that might help you:
[http://www.aboutdebian.com/proxy.htm](http://www.aboutdebian.com/proxy.htm)
[http://www.aboutdebian.com/firewall.htm](http://www.aboutdebian.com/firewall.htm)

Also check out shorewall or firestarter
[http://www.shorewall.net/](http://www.shorewall.net/)

Chears 
idipous

---

