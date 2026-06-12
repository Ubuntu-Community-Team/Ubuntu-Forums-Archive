---
title: "How to change mac address during minimal install"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by eXecu7or on 2009-10-28
Hi,

I'm trying to do a minimal over the internet installation using the 9.04 mini.iso.

I need a way to change the mac address of my nic so that it is correctly configured during the first stages of the text based install, since on my network DHCP needs the correct mac address in order to set up the corresponding ip, gateway, etc.

At the moment, I am able to configure it via the text menus and then edit /etc/network/interfaces via shell + nano and add "hwaddress ether".

However, I am unable to restart the network since both init.d/network and ifconfig are missing from the minimal shell available during installation.

Is there any way to restart the network via minimal shell? Or any other way to change the mac address?

---

