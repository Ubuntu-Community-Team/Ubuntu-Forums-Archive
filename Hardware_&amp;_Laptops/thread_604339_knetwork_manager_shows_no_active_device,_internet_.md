---
title: "knetwork manager shows no active device, internet still working fine though"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by agent-s on 2007-11-06
Obviously this bug is not that serious but it still is improper performance.  After I installed deluge then removed it, Knetwork manager refuses to see my network card.  However, going through the network devices dialogue and manually setting it dhcp and enabling it worked for me.  Is anyone else getting this?  or is it an error on my part?

---

### Post by ROBarber on 2007-11-06
Hello.

on a terminal try this command (with sudo if you are not a root)

nano (or gedit) /etc/network/interfaces

and look if can find something like 'auto eth0'.

also for upping the network card you can use the following command:

ifconfig eth0 (or wifi0) up.

I'm here if you won;t solve this issue

---

### Post by agent-s on 2007-11-06
the network card works fine under linux, the problem is knetworkmanager

thx tho

---

### Post by govath on 2008-02-27
Hello.

open a terminal and write command 

sudo nano /etc/network/interfaces

and just remove everything from that text and it will reset the settings to default
 
it worked for me !!

Thanks.

[http://govath.wordpress.com]("http://govath.wordpress.com")

---

