---
title: "Ubuntu Install Trouble Laptop"
date: 2017-06-12
forum: Hardware
---

### Post by apol1 on 2017-06-12
Hello Im attempting to install Ubuntu 16.04 on an Asus Gaming laptop (republic of gamers) modle number G55V

Its running an intel Intel Core i7-3720QM with an Nvidia GEFORCE GTX660M

Installing from a flash drive I seem to be experiencing graphics issues, the keyboard becoming unresponsive, and a purple screen of death.

Can anyone help? Or perhaps a recommended article I should read?

Thanks in advance :)

---

### Post by kc1di on 2017-06-12
You will need to add ```
nomodeset
``` to the boot line in Grub. and then install the right driver from the driver manager. 

Nvidia cards are a little tricky to get going but usually will work well once the right driver is installed. 

[This page]("https://linuxmint.com/rel_serena_mate.php") will help (it is written for Mint but will still work with Ubuntu.) go to the section called solving Freezes. Good Luck.

---

