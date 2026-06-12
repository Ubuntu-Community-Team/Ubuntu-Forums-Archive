---
title: "nic enabling problem with masterpiece 25340 gericom"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by dpurple77 on 2005-12-29
Hello everyone.
I am a very happy ubuntu user on my two basic desktop machines and wanted to install it to my gericom masterpiece 25340 laptop. everything went great and everything was found and configured but the ethernet. the nic is a sis900 which is nicely found under ifconfig eth0 and it is installed as it shows in lsmod. but when i try to enable it (lo is enabled only by default) i get a SIOCSIFFLAGS: Device or resource busy message. after lots and lots of searching i really didn't find anything as a solution except disabling pnp on bios. the problem is that the bios doesn't give me a choice for that. it is really basic with no options except boot order. the only choice it has is about installed os with XP/OTHER. both bring the same error on enabling the nic. any ideas would be greatly appreciated. i even gave grub a pci=biosirq which i found somewhere which didn't help at all. any idea on disregarding the pnp bios on boot up or any other solution to my problem would be nice. i dont want to stick to windoze for this. thanx in advance.

---

