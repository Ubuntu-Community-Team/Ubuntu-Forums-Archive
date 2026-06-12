---
title: "realtek 8187b and WPA"
date: 2008-06-08
forum: Hardware
---

### Post by secureboot on 2008-06-08
I'm trying to get the wireless card in a Toshiba Satellite a215-s7422 laptop working.

It shows up in lsusb correctly.

I've seen the drivers at [http://www.datanorth.net/~cuervo/blog/](http://www.datanorth.net/~cuervo/blog/).  They work just find in the 2.6.24 kernel with the patch, except for WPA support.

If I turn WPA off, the laptop connects to the network appropriately.  My AP is an Apple Time capsule, which works fine with all other devices I've seen.  However, when I put in the network password into networkmanager, no connection is established.

Is the solution here to use WPA_supplicant?  Isn't this what network manager uses by default?

Anyone else have success with 2.6.24 kernel and WPA with this chipset?  There is a lot of info out there about getting this chipset to work initially, but I haven't seen any description on how to get WPA working...

---

### Post by secureboot on 2008-06-08
Also, I've tried the instructions here:
[http://www.sabayonlinux.org/forum/viewtopic.php?f=52&t=13077](http://www.sabayonlinux.org/forum/viewtopic.php?f=52&t=13077)

Again, I can connect without security, but no luck with WPA enabled.

Any ideas?

---

