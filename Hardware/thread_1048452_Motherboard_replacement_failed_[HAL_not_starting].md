---
title: "Motherboard replacement failed [HAL not starting]"
date: 2009-01-23
forum: Hardware
---

### Post by phoenixdown83 on 2009-01-23
Hi all,

I'm not a linux expert. I have searched my problem across the internet but did not find a suitable solution.
I have a trouble in reconfiguring my (k)ubuntu system after having replaced the motherboard with another "identical one".

I have kubuntu 8.04 installed over an m1710 laptop, 4 Gb of RAM.

the system worked fine before the change. after i notice these issues:
- the network card was to reconfigure
- ifconfig -a shows eth1 (and i suppose it should also show eth0)
- kpowersave is not working-

the last issue is the worse. I have discovered that HALD is not starting. I have double checked the configuration and I cannot find any problems into the logs.

no hal* process is active.

if I manually start /etc/init.d/hal start everything works fine.

Can anybody help me in fixing this nasty problem. probably is really silly, but I have no enough knowledge to do that.

Thanks,
Phoenix Down

---

