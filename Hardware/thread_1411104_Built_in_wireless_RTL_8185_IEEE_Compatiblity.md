---
title: "Built in wireless RTL 8185 IEEE Compatiblity?"
date: 2010-02-19
forum: Hardware
---

### Post by Ammon Van Meter on 2010-02-19
Hello. I am trying to install my INF using the NDIS wrapper. The INF is installing, but it is not detecting the prescence of the hardware. In windows, I have to install the motherboard before the Wireless is detected. What are the odds I have to do this in Hardy as well? The closest to compatibility is 8180 I have found.

I am also somewhat of a noob. I know my way around the gui somewhat, but terminal commands still elude me.

My laptop is a gateway 3228.

Thanks for any help in advance.

---

### Post by IcarusR on 2010-02-20
Once the desktop is up & running in Ubuntu all relevant mobo chipset modules (drivers) are loaded so should not need to load more to get wifi module to install.

The RTL8185 works under ubuntu. 

From what I understand the module should be in the current kernel & loaded at boot.

Failing that look at this post, 8 + 9 suggesting installing "backports modules generic" package to get module in Hardy.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8575696#8]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8575696#8")

---

