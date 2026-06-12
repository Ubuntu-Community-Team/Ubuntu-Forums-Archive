---
title: "Toshiba Tecra A4 Network card"
date: 2006-05-11
forum: Hardware &amp; Laptops
---

### Post by am_abdelsalam on 2006-05-11
SA 

I've just installed ubuntu linux on my Tecra A4 laptop and I cannot connect to network at my office. we have DHCP server and I configured the ethernet to automatically obtian network information. but it couldn't connect to the network.

I've installed mandriva before ubuntu and the solution is to disable ACPI service. but i don't know how to disable this service in ubuntu. please help....



thanks

---

### Post by Xoctor on 2007-06-14
Solution is here: [https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4)

Basically, upgrade your BIOS to 1.70, then put the following in your kernel parameters (specified in /boot/grub/menu.lst) pci=noacpi irqpoll

Finally!

---

