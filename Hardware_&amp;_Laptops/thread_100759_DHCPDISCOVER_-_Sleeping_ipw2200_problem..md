---
title: "DHCPDISCOVER - Sleeping ipw2200 problem."
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by KasperTech on 2005-12-08
Hi all.
I have managed to get the ipw200 driver version 1.0.8 to work, along with the newest firmware (2.3 I think) but my wireless network does still not work :( I've compiled the driver in /usr/src/ipw-[version] and moved the firmware into /usr/lib/hotplug/firmware and everything... but when I unplug the cable and deactivates the eth0 and activates the eth1 under Network Settings, it fails. I'm able to find my network, and it says that signal is 100% so no problem there. But if I first run the command "sudo ifdown -a" to free the network instances and then the command "sudo ifup -a" to renew DHCP and so on, it goes:
> ipw2200 on eth1:
DHCPDISCOVER: 255.255.255.0 interval [random number]
DHCPDISCOVER: 255.255.255.0 interval [random number]
DHCPDISCOVER: 255.255.255.0 interval [random number]
...
No lease. Sleeping

"lsmod|grep ipw" returns both the firmware and several ipw2200 instances :confused: ?

I'm getting desperate, please help me!!!
I can offer SSH access if required.

--
Regards Kasper.

---

### Post by fdimmling on 2005-12-10
Why did you compile the ipw2200 driver? The ipw2200 is supported by the custom kernel and should work out of the box including WPA. No need to put any firmware anywhere by yourself.

Friedrich:???:

---

### Post by KasperTech on 2005-12-11
[QUOTE=fdimmling]Why did you compile the ipw2200 driver? The ipw2200 is supported by the custom kernel and should work out of the box including WPA. No need to put any firmware anywhere by yourself.

Friedrich:???:[/QUOTE]

Hi Friedrich.
I compiled the newer ipw2200 driver, because the one that ships with Ubuntu 5.10 is **sucky**. It closes the connection randomly and does not run smoothly at all. The firmware update was required in order to make the new driver work.

---

### Post by fdimmling on 2005-12-13
[QUOTE=KasperTech]Hi Friedrich.
I compiled the newer ipw2200 driver, because the one that ships with Ubuntu 5.10 is **sucky**. It closes the connection randomly and does not run smoothly at all. The firmware update was required in order to make the new driver work.[/QUOTE]

Strange, I'm using the standard kernel ipw2200 support on my Acer Travelmate 291LCi every day and I never got any problem. Stable connection even with heavy traffic on NFS file transfers and for many hours continuously, WPA works fine. 

Friedrich

---

