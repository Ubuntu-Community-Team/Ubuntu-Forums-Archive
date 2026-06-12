---
title: "motorola sm56 pci modem"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by mike2005 on 2005-04-26
Hi if anybody can help it would be really appreciated. I have a swann swannsmart II pci modem which I think is in fact the motorola sm56 pci modem. I am 90% sure of this. 

I went to the motorola site and downloaded the following sm56 driver rpm packages. I  was not sure which linux version to get. It has mandrake, redhat, and suse and multiple versions and cpu version of each. I chose however the intel version when available as i have an intel celeron 2.4Ghz.

I loaded up ubuntu and logged in as root. Put the files in the temp folder etc.
It said I needed to use "ALien" instead of rpm -i

So I used Alien -i with each. IT would do something for a minute, not come up with any errors and give me no messages, just return to the terminal.

I have rebooted and my pci device which has attributes such as "motorola" but is classified as unknown still does not work. I do not know what further steps to take, if any of these version are compatible with ubuntu, etc. I can find no information related to this.

I really need to get the modem working, or I can't update ubunti. I am unable to find any information whatsoever on how to manually install packages in ubunti (by reading from my windows volume and copying the file into linux as opposed to downloading)...

Thanks if anybody can help me get this modem working. 

Michael

---

### Post by az on 2005-04-26
Motorola does not care about open source.  Their driver is 
1.  Really old and was never stable.
2.  Not for 2.6 kernels
3.  Precompiled against an older Red Hat, Suze or mandrake kernels.  They never made a real effort to make the driver available to all linux users.  They have long abandoned development of the driver.  They do not support linux.

Your modem will not work in Ubuntu.  You can buy a cheap lucent or intel based modem for about ten bucks.  You can also buy a hardware modem and be sure to never have problems.

If you are 90 percent sure that is what model you have, you can double check by running the scanmodem script from linmodems.org.

---

### Post by mike2005 on 2005-04-26
Thats cool then. When I get the opportunity I shall express my affections for motorola products with my wallet...

---

