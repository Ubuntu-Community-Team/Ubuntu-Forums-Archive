---
title: "eth0 and eth1 switch after suspend"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by kluut on 2005-04-11
Hi,
I have a Dell latitude 600, and Ubuntu Hoary provides the best out-of-the-box hardware support of all linux distributions I have tried. So I am quite happy with it. However, there is one strange problem: 
I have a broadcom ethernet card (tg3 kernel module), which after a clean boot is always detected as eth0, and a centrino wireless (ipw2100 module), which is eth1. But after a suspend-to-ram, eth0 and eth1 are sometimes (not always) switched! Of course, this messes up the network configuration. I can quite easily solve it by interchanging eth0 and eth1 in /etc/network/interfaces, and run /etc/init.d/networking restart. But I was wondering if someone knows a way of defining somewhere which card is which, to prevent the switch.
(Note: I do have to remove the ipw2100 module before suspending by having the line MODULES="ipw2100" in /etc/default/acpi-support. I don't know if that could have something to do with it...)

---

### Post by odix on 2005-04-11
[QUOTE=kluut]Hi,
I have a Dell latitude 600, and Ubuntu Hoary provides the best out-of-the-box hardware support of all linux distributions I have tried. So I am quite happy with it. However, there is one strange problem: 
I have a broadcom ethernet card (tg3 kernel module), which after a clean boot is always detected as eth0, and a centrino wireless (ipw2100 module), which is eth1. But after a suspend-to-ram, eth0 and eth1 are sometimes (not always) switched! Of course, this messes up the network configuration. I can quite easily solve it by interchanging eth0 and eth1 in /etc/network/interfaces, and run /etc/init.d/networking restart. But I was wondering if someone knows a way of defining somewhere which card is which, to prevent the switch.
(Note: I do have to remove the ipw2100 module before suspending by having the line MODULES="ipw2100" in /etc/default/acpi-support. I don't know if that could have something to do with it...)[/QUOTE]
 I think, the best way to solve this is to let udev decide the the network adapters names, this could be done with udev rules. I will try this today in the evening to give a more precise reply

odiX

---

### Post by alastair on 2005-04-11
I wasn't aware that udev dealt with network devices (well, bar /dev/net/tun). After all, eth0 is not a /dev device.

The allocation of an ethernet device name (eth0, eth1) is dependent on module load order and/or options. I think the ipw driver (at least used to) lets you specifiy the actual device name (i.e. eth1/wlan0 etc.).

Alternatively, try using the "hwaddress" (in /etc/network/interfaces) - see : man interfaces.

Other options - ifrename (man ifrename).

---

### Post by odix on 2005-04-12
recent releases of udev, and I think the version of udev which comes with hoary is able to handle network dervices.
Here is an example of a rule with the network address as a key (taken from the  [gentoo-wiki](http://gentoo-wiki.com/HOWTO_Customizing_UDEV) )

KERNEL="eth*", SYSFS{address}="00:52:8b:d5:04:48", NAME="lan"

odiX

---

### Post by kluut on 2005-04-12
Thanks for the feedback!

I did add the udev rule, I tried both making a file /etc/udev/rules.d/network.rules that consists of the line
KERNEL="eth*", SYSFS{address}="00:04:34:4D:6F:ED", NAME="lan"
and adding this line to an existing rule file. Unfortunately, neither of these seem to have any effect on the name of my network cards. The wlan card is still called eth1 (or eth0) So maybe hoary's udev is not new enough to include the network cards...

---

### Post by odix on 2005-04-12
Yes, you are right, but I found the reason  :smile: 
maybe /etc/iftab overides the rules. I've mad some tests with modifying /etc/iftab and found out that only eth*n* names are recognized in the network setup. Maybe this will help you.

odiX

---

