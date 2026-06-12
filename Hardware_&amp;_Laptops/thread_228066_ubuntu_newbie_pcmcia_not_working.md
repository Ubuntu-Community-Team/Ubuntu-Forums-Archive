---
title: "ubuntu newbie: pcmcia not working"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by cty on 2006-08-02
Hi,
I'm new to ubuntu, so excuse me for my stupidity...
I've install ubuntu 6.06 on a olde Dell notebook which used to be running FC5. Everything seems to be working fine except I can't get it to recongize the pcmcia nic card. I've tried the following:
linksys 10/100 + 56k combo
3Com 3c575 10/100 cardbus
under FC5, with NetworkManager (service NetworkManager start), it will knows that I've a pcmcia nic inserted and the nic will then connect. for example, 3c575 will come up as eth1 on the old FC5 setup. Of course, it is now debian based, so I dont think I've `NetworkManager' anymore. What is the equivilant in ubuntu?
And how do I teach the box to use my pcmcia nic?
BTW, when I do `lsmod', it shows that pcmcia_core is loaded... that 's what I think I needed... 

thanks,
cy

---

### Post by K.Mandla on 2006-08-03
Depending on how old your laptop is, you might be having this problem. ...

[http://www.ubuntuforums.org/showthread.php?t=125334](http://www.ubuntuforums.org/showthread.php?t=125334)

However, if it was working under FC5, it should be working under Dapper. 

I believe this is the NetworkManager you mention, but I haven't used it so I'm not entirely sure.

[http://packages.ubuntu.com/dapper/net/network-manager](http://packages.ubuntu.com/dapper/net/network-manager)

Unless I'm mistaken, you could also try *cardctl ident* and *cardctl info* commands from the terminal, to try and get some information out of the PCMCIA ports. Good luck!

---

