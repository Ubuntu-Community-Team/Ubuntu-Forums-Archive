---
title: "IPforwarding"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by egilj on 2005-08-21
I have a Fujitsu Siemens Amilo 1425 running Hoary, and I like it a lot. For internet connection I use a SonyEricsson GC85 Edge card, which works fine. I would like to let my small home network share this connection, because in the end it will be a bit quicker than the ISDN-connection that I have there. The problem is that it will not work.

/etc/network/options has been changed so that ip_forward=yes. If I do

less /proc/sys/net/ipv4/ip_forward

I get 1.

I have the Shorewall firewall running, and it has been configured for internet sharing. It can't be the problem, because even if I do *shorewall stop* and *shorewall clear* I am only able to ping to my laptop, not to the outside.

Any suggestions would be welcome!

---

### Post by jasmuz on 2005-08-21
Have you installed a DNS resolver, if not then install dnsmasq wich will do dns and dchp for you.

Im running Guidedog (similar to shorewall) and dnsmasq to share my connection and it goes smooth, remember to specify the other computer to use your ip as its gateway.

---

### Post by egilj on 2005-08-21
[QUOTE=jasmuz]Have you installed a DNS resolver, if not then install dnsmasq wich will do dns and dchp for you.

Im running Guidedog (similar to shorewall) and dnsmasq to share my connection and it goes smooth, remember to specify the other computer to use your ip as its gateway.[/QUOTE]
 I will try. Thanks a lot!

---

### Post by s_p_a_r_k_y on 2005-08-21
do you have iptables set to masquerade the packets? I can't route until I enter the following command

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

---

### Post by egilj on 2005-08-21
[QUOTE=s_p_a_r_k_y]do you have iptables set to masquerade the packets? I can't route until I enter the following command

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```[/QUOTE]
 That solved it. I just swapped eth0 with ppp0 and it worked. Thanks to both for your advises!

---

### Post by s_p_a_r_k_y on 2005-08-22
when I first started out using linux as a router/gateway the 2.4 kernel was still young and there was no little documentation out there for IPtables...took quite a while to figure out the syntax. remember to save you iptables session so when you reboot, you don't have to retype that command or save the command in a text file and make it executable for whenever you reboot.

---

### Post by juan,paredes on 2006-02-05
This is off-topic but would you please post how you configured your gc85? I've tried several alternatives, including [http://www.ubuntuforums.org/showthread.php?t=47305&highlight=gc85](http://www.ubuntuforums.org/showthread.php?t=47305&highlight=gc85), but no luck yet...

Thanks a lot!!!

---

