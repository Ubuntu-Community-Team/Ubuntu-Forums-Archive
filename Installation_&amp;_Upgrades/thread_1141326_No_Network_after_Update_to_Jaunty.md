---
title: "No Network after Update to Jaunty"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by TMW on 2009-04-28
Hi,

I updated a Lenovo Thinkpad T400 from intrepid to jaunty today, and afterwards my Network (eth0) was gone. Altough the device shows up in ifconfig, and seems to be working, I don't get an IP adress by DHCP. 

The device is an Intel 82567LM (rev 03) Gigabit Network Controller.
Module e1000e is loaded but not used (lsmod output:  e1000e   121136   0)

Thank you for your help,


Tobias

---

### Post by jenks on 2009-04-28
Make sure that the lines:

auto eth0
iface eth0 inet dhcp

in your /etc/network/interfaces are present and uncommented, then restart networking. I found the second line commented out after upgrading my system - a very silly thing for the updater to change!

---

### Post by TMW on 2009-04-29
I checked the network interfaces file. eth0 is up according to ifconfig. however, i don't get an IP adress. neither by network manager, nor by dhclient or ifup/ifdown scripts

---

