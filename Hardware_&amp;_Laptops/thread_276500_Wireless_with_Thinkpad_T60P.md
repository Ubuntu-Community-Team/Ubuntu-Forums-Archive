---
title: "Wireless with Thinkpad T60P"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by grado on 2006-10-13
Hello,

I installed Ubuntu Dapper on my pristine new T60P. When I enable the wireless interface it detects the network and gets connected. But I am unable to access the internet or ping to any machine. The gnome connection properties applet shows me that my card is continuously receiving packets but not sending any.

Some details:
$ sudo lsmod | grep ipw
ipw3945      132349 1
ieee80211     38952 1 ipw3945

$ sudo lspci | grep -i "network controller"
0000:03:00.0 Network controller: Intel Corporation: Unknown device 4227 (rev 02)

Please help!

Thanks.

---

### Post by IcemanV9 on 2006-10-13
Check your /etc/resolv.conf file.

You may want to try this -> sudo ifdown eth1; sudo ifup eth1 (I assumed eth1 is your wireless device)

Also, install **[COLOR="Orange"]*[network-manager]("https://help.ubuntu.com/community/WifiDocs/NetworkManager")*[/COLOR]**. Network-manager is an application to make (wireless) networking "Just Work".

---

