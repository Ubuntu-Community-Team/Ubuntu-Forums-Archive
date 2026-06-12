---
title: "Recent update on Thinkpad t14s (AMD), laptop screen now just shows static"
date: 2022-01-19
forum: Hardware
---

### Post by kilowt on 2022-01-19
Just installed a stack of updates on Kubuntu 20.04. KDE Plasma 5.18.5, KDE frameworks 5.68.0, kernel version 5.13.0-27-generic. The laptop is a Ryzen 7 4750OU, Radeon. After the required reboot, the screen starts outputting static after going through normal posting, grub screen, etc. I assume since the screen only stops working once Kubuntu fires up it's probably a driver issue? Fortunately I mostly use this machine as a desktop with a couple monitors connected but I'd like to figure out what broke and get it sorted. I'm sure I need to provide additional details, happy to do so if someone will provide the commands.

---

### Post by sposhua on 2022-01-20
I have a similar issue, in my case [normal flavour] Ubuntu starts up but crashes and shows "static" on the screen when I close the lid or lock. Also Ryzen 7 with Radeon (Slimbook pro). If I plug in an external screen that one works and I can log in again, but all open apps forced closed and laptop screen still shows static. If I have an external screen plugged in before I lock the same happens, but all open apps stay open.

---

### Post by sposhua on 2022-01-21
Seems like they are on the case: [https://bugs.launchpad.net/ubuntu/+source/linux-hwe-5.13/+bug/1958412](https://bugs.launchpad.net/ubuntu/+source/linux-hwe-5.13/+bug/1958412)

---

### Post by kilowt on 2022-01-21
Great, thanks for the link!

---

