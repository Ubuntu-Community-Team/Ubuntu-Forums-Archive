---
title: "How do you set a timeout on the DHCP network"
date: 2005-11-29
forum: General Help
---

### Post by gnutux on 2005-11-29
Hey all!

I run Kubuntu on my laptop and sometimes it never has a network connection, so how do I set the timeout for the network interface to 5-10 seconds?

Thanks,
gnutux

---

### Post by greenway on 2005-11-29
Exactly what do you mean by "a timeout for the network interface"?

---

### Post by gnutux on 2005-11-29
so that when the computer is booting, it will not take forever to try to find a DHCP server and obtain an address.

gnutux

---

### Post by greenway on 2005-11-29
If you're talking about the DHCP lease time, you will have to configure your DHCP server to advertise new leases every few seconds, but are you sure that's want you want. I am not sure about this, but this might slow down your networking speed since you NIC has to apply for a new lease every few seconds...

For the above, the way to do it depends on your DHCP server; is it a hardcoded router? If so, which brand? Or are you using a software router?

However, your lease time doesn't influence your network connection on boot; when your NIC is loaded it should look out for the DHCP server on it's own and request a lease (ip/netmask, gateway, dns servers). It sounds to me that the problem is with your host trying to connect to the network, not with your DHCP server.

---

### Post by gnutux on 2005-11-29
sorry, that's not what I meant, I meant on the computer (client). When booting, I don't want Kubuntu to try to find the dhcp server forever. How do I set a timeout for the waiting? I want to shorten it from 30s to 5s.

gnutux

---

### Post by bruce147 on 2005-11-29
I think what you want is /etc/dhcp3/dhclient.conf
then find the line
#timeout 60;
uncomment it and change it to 10 seconds for example
timeout 10;
You can also hit control+c during the boot  process to skip that item.

I just searched this forum with keywords "dhclient.conf timeout" and apparently some people have more elaborate procedures for this

---

### Post by gnutux on 2005-11-29
thx, it worked ;)

gnutux

---

