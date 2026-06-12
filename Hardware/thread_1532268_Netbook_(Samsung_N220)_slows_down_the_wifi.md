---
title: "Netbook (Samsung N220) slows down the wifi"
date: 2010-07-16
forum: Hardware
---

### Post by joschaef on 2010-07-16
Hello everybody!

I encountered a really odd problem with my new netbook.

I am running Ubuntu 10.04 on a Samsung N220 Mito. So far everything worked fine.

Now I tried the machine for the first time in our work group where we have a wifi (with internet access) for all laptops. The wifi is controlled by a computer running Suse 9.3 which provides a DHCP server and imposes a firewall. Sometimes we encountered already, that the wifi is slow for no real explanation, and we tried to "fix it" by replugging the wifi access point which is connected to the dhcp/firewall server. 

At the moment there is only a macbook in the wifi, where no problems with the internet or wifi connection are encountered.

Now coming to my actual problem: In addition to the macbook i connect the Samsung N220 to the Wifi. 

1. Problem: 
My download speed is for some reason limited to 70KB/s max. This is neither a limitation of the server/website i browse on, nor a configuration of the netbook: at home i have > 500KB/s download speeds. Furthermore, it is not a default limitation for "untrusted" or "new machines" in the wifi, as for instance other new laptops get full speed internet with our wifi.

2. Problem:
Once the Samsung N220 is generating traffic in the wifi, the wifi is slowed down dramatically for all other machines: I run a ping to the router from the macbook. The ping times with the N220 ideling are 2-6ms. When I start downloading or browsing in the web with the N220 the ping speed drops to > 800ms. Vice versa, when the macbook is generating the traffic the ping of the N220 to the rooter stays constant at around 2-6ms. So clearly, it is some problem originating from my netbook or maybe its treatment in the wifi.

Sorry for the long text, and thanks for any help or idea!

---

### Post by joschaef on 2011-02-09
Problem fixed. The cause was the Linksys Access point WAP4400N. With a firmware update I could fix the problem.

---

