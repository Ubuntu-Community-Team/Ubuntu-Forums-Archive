---
title: "Firewall Questions"
date: 2008-07-29
forum: General Help
---

### Post by Ollie A on 2008-07-29
Just a couple of questions about the firewall...

1. Does Ubuntu have a firewall enable automatically by default?
2. Does Ubuntu have a firewall?
3. How do I access firewall settings?

Thanks :)

-Ollie

---

### Post by dexter.deepak on 2008-07-29
ubuntu has a firewall enabled by default, and you need to use iptables as a tool to access it.
a better gui approach is 'firestarter'

---

### Post by Ollie A on 2008-07-29
How do I use iptables to turn it off?
The exact command would be nice :)

-Ollie

---

### Post by dexter.deepak on 2008-07-29
its better to do so by using firestarter...it has a simple gui.
iptables are pretty complex. for the moment you can try:
```
sudo iptables-save > /root/firewall.rules
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo iptables -t mangle -F
sudo iptables -t mangle -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
```
to reactivate:
```
sudo iptables-restore < /root/firewall.rules
```

---

### Post by Ollie A on 2008-07-29
Brilliant, thanks for the awesome help :)

-Ollie

---

### Post by bodhi.zazen on 2008-07-29
Firestarter is a little out of date.

Ubuntu 8.04 + comes with ufw

I am sure ufw will have a gui interface soon, but in the mean time it is more powerful then firestarter, more secure, and very easy to use.

 [uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

