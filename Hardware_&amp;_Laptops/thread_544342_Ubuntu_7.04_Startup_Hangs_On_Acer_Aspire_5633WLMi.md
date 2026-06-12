---
title: "Ubuntu 7.04 Startup Hangs On Acer Aspire 5633WLMi"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by Tridion2000 on 2007-09-06
I bough an Acer Aspire 5633WLMi laptop which came preinstalled with Vista Home Premium. I got so fed up with it, I decided to try Ubuntu. The Live CD loaded fine and I could get on the internet no problem. So I decided to install it, removing Vista in the process.

Installation went fine, but on restarting it, it just hangs during startup. It seems to be on the bit "Configuring Network Interfaces".

Any ideas how to solve this?

---

### Post by Tridion2000 on 2007-09-06
I have semi sorted this by commenting out all the entries in /etc/network/interfaces other than etho0 as I am currently using a wired connection to my router.

However, at some point in the future I would like to use wireless but suspect the hang will return if I uncomment that entry.

Any solution?

---

