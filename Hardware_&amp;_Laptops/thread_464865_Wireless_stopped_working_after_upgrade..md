---
title: "Wireless stopped working after upgrade."
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by Pathian on 2007-06-05
I recently upgraded my system from Dapper to Edgy and from Edgy to Feisty using the update-manager -c command. The first upgrade went smoothly, but after the second upgrade, my wireless stopped working. Network applet on my bar "sees" my wireless network, but will not connect to it. Can anyone help me out in terms of finding a solution?

Here are the details:
My wireless card is an integrated card.
LAN-Express AS IEEE 802.11a/b miniPCI adapter (or rather, that is the name listed in my windows dev managers)

My mobo/chipset is the
Intel 852/855 GM/GME Chipset

Other possibly relevant details are that after starting up for the first time after the second upgrade, I received a warning (for the first time) that Ubuntu was using "restricted drivers" and one of the drivers listed was the Atheros Hardware Abstraction Layer (HAL) driver. I know this is a wireless driver, but I'm not sure why it's in use since to the best of my knowledge my wireless does not have an atheros chipset.

I tried booting to my earlier version of the kernel to see if it was a kernel update that made it stop working, but it was the same. I have a feeling it is some package that installed in the update that superceded my old working wireless drivers, but I don't know which package it was or how to roll it back.

Any input would be welcome, thanks much,
Justin

---

