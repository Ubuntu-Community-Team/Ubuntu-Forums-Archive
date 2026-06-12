---
title: "Ethernet problem"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by linuxfornick on 2005-10-25
Hi 
I'm new to Linux.I have just installed Ubuntu on my machine with onboard LAN card.It does not seem to recognize the eth0.It only shows loopback.
Will
# sudo ifdown eth0
# sudo ifup eth0
this help.
Cannot configure IP address and dns for my DSL connection.
Please help
Thanks in Advance

---

### Post by linuxfornick on 2005-10-25
I'm sorry if i've posted the thread in the wrong forum.
It should have gone in the absolute beginners forum 
any help will be appreciated.

---

### Post by xprisoner on 2005-10-25
What brand system/motherboard do you have? If we can figure out what chipset your onboard ethernet uses we can figure out what module you need to have loaded.


Post the output from "lspci".

---

