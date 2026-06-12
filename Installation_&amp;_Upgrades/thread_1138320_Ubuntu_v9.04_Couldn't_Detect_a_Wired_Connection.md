---
title: "Ubuntu v9.04 Couldn't Detect a Wired Connection"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by corsairgt on 2009-04-26
Ubuntu v9.04 and 8.04 couldn't connect to the Internet by LAN cable if the router LAN IP address 192.168.2.1 is used. A wired connection is possible only if the address is changed to 192.168.1.1. Does anyone know why?

My router doesn't allow me to change the IP to 192.168.1.1.

---

### Post by Triptol on 2009-04-26
Just guessing, but it looks like your network card is set to a preconfigured IP address (compared to a DHCP address).

You could check the following file and see what settings it has for eth0:
```
/etc/network/interfaces
```

If the settings for eth0 look like this:
```
auto eth0
iface eth0 inet static
        address 192.168.1.x
        netmask 255.255.255.0
        gateway 192.168.1.1
```

you have configured your card for a static IP. You might want to change that to a 192.168.2.x. Afterwards you need to following two commands to restart the networkcard:
```
ifdown eth0
ifup eth0
```

If your routers supports DHCP, you could also set your network card to automatically receive an IP from your router. The settings for eth0 in your /etc/network/interfaces should then look like this:

```
iface eth0 inet dhcp
```

Now if you have setup your networkcard for DHCP and you are getting a wrong address, you've done something wrong. You should then check your router's settings for DHCP and make sure it gives the right address.

Hope this helps.

---

