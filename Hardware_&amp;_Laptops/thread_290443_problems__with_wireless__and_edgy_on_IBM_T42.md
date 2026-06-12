---
title: "problems  with wireless  and edgy on IBM T42"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by balki2005 on 2006-11-01
Hello,

I can't see my wireless card in edgy, but I when I install  edgy  i saw my wireless card and could make a connection with my wireless network. after installation was my wireless card gone ?? and could not select it on network-manager under gnome?

on dapper it works fine and on previous releases of edgy also?? what  goes wrong ? who  can help me  ?

thanks in advance,

Balki2005

---

### Post by balki2005 on 2006-11-02
I found  the  solution !! :) 

you need  to  install  the  restricted  modules  and then  I  can use  my wirelesscard.
I installed  there after the  network-manager. And  it works  smoothly  !!But  you  need  first make  /etc/network/interfaces  empty.  otherwise  network-manger  will  not  work like  it must.

balki2005

---

### Post by spaceghoti on 2006-11-06
Restricted modules?  What are their names?  My internal wireless is appearing in the network configuration, and I can even set it up to a manual IP and ping the router.  Unfortunately, I can't get outside the network, and it will never take a dynamic IP.

---

### Post by spaceghoti on 2006-11-24
Okay, due to an xserver error I ended up rebuilding the laptop, this time making sure I installed knetworkmanager and network-manager after I deleted /etc/network/interfaces.  After reboot, interfaces came back and I enabled DHCP in the wireless connection.  It immediately connected to my local network.

---

