---
title: "Configuring network interfaces - Taking too much to load"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by arrizaba on 2005-04-11
Hi,

The title says it all: [COLOR=Teal]Configuring network interfaces - Taking too much to load[/COLOR]

Actually, it's taking longer and longer as time passes by...I hoped that the problem would dissapear with Hoary, but it hasn't. It's actually worse. Does anyone knows how to solve this?

---

### Post by alastair on 2005-04-11
No idea. But you give next to no details ....

Wired? Wireless?
Load? You mean network startup at boot?
Where is it sticking? DHCP?
Anything interesting in the logs? (/var/log/syslog)

---

### Post by dejitarob on 2005-04-13
I had this same problem. If you want a temp fix you can always just hit ctrl+c to bypass it. For a permanent solution, if you have a laptop or two network cards, the one that is not in use is most likely looking for a dhcp server for an ip address and cannot find one. Therefore the boot process is waiting for it to timeout. Doing a 'sudo gedit /etc/network/interfaces' and commenting out (with #) the network card that is not in use (eth1 for example) should solve the problem if this is the case.

---

### Post by dejitarob on 2005-04-15
You can also try setting the DHCP timeout lower from the default of 60 which is too long, IMO. 'sudo gedit /etc/dhclient.conf' then uncomment 'timeout=60'. I have mine set to 10 since the networks I am usually on are relatively fast but 15 is probably safer. To look at the available options in greater detail use 'man dhclient.conf'.

---

### Post by arrizaba on 2005-04-19
Thanks a lot!

That was the solution I was looking for, setting the timeout lower works nicel. I use one card at work (eth1) and the other at home (eth0), so i did not want to disable one of them.
Nice "Guernica" avatar you got, dejitarob.

---

