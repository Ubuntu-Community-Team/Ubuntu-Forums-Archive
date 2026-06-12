---
title: "slow boot time - network detection"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by JackDog on 2005-12-08
I have setup ubuntu on the laptop to use Network Manager. This works great except the system still attempts to detect anyway on boot. What is the best way to setup ubuntu to where it simply uses Network Manager and does not try to configure the network on boot?

I edited /etc/network/interfaces and removed the auto lines but this has no effect.

---

### Post by noob_Lance on 2005-12-09
jsut hit ctrl+c and interupt it during the boot... thats what i do everytime until i can figure out a better method i guess..

---

### Post by lcg on 2005-12-09
[QUOTE=JackDog]I have setup ubuntu on the laptop to use Network Manager. This works great except the system still attempts to detect anyway on boot. What is the best way to setup ubuntu to where it simply uses Network Manager and does not try to configure the network on boot?[/QUOTE]
I don't know Network Manager. However, I really like ifplugd, which only brings up interfaces once they are connected.

[QUOTE=JackDog]I edited /etc/network/interfaces and removed the auto lines but this has no effect.[/QUOTE]
IIRC, hotplug also brings up network interfaces. 'sudo dpkg-reconfigure hotplug' and choose to bring up only interfaces with a 'mapping hotplug' line. That should solve your problem.

HTH,
Lars

---

