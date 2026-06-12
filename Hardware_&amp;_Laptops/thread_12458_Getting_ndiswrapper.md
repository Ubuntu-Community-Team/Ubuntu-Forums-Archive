---
title: "Getting ndiswrapper"
date: 2005-01-24
forum: Hardware &amp; Laptops
---

### Post by mc_03 on 2005-01-24
Hi,
I just installed Ubuntu on my brother's PC, which has a wireless card supported by ndiswrapper. But I obviously can't use apt to get the required packages without a working  connection to the internet. I also can't just stick the source code on a floppy and compile it, because I would need the kernel source and development tools which I also can't get with no internet connection! Any Ideas?
Thanks!  :-k

---

### Post by Sham on 2005-01-24
Hehe, my uncle was going mental over the same thing! I think they need to address this in the next release (if they can). 

Is there any reason why you can't plug into your wireless router with a network cable?

---

### Post by az on 2005-01-24
"because I would need the kernel source and development tools which I also can't get with no internet connection!"

sudo apt-get install build-essential linux-headers-2.6.8.1-3-386

Its all there, on the cd.

---

### Post by mc_03 on 2005-01-24
Ah, that worked. Thank you  8-)

---

