---
title: "BCM4328 with 2.6.24-rc3"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by punischdude on 2007-12-05
Hi there,

I' ve recently build the 2.6.24-rc3 kernel prepatch using Gutsy in order to get my BCM4328 wireless adapter working on my HP Pavilion dv9533eg without using ndiswrapper.

But it does not work as expected. The Adapter is recognized, as I can see in the lspci output, but it's not listed in iwconfig or ifconfig.

Some details: 
[lspci -vv]("http://ubuntuusers.de/paste/19304/")
[lsmod]("http://ubuntuusers.de/paste/19305/")
[.config]("http://ubuntuusers.de/paste/19306/")

Any ideas?

Thx
punischdude

---

### Post by Ayuthia on 2007-12-05
According to the b43 website, it does not look like your card is supported yet.  Here is the link to their site:
[http://linuxwireless.org/en/users/Drivers/b43#unsupported](http://linuxwireless.org/en/users/Drivers/b43#unsupported)

If we were to assume that it works, it looks like you have not added the b43 module as of yet.  b43 should have shown up in lsmod.

---

