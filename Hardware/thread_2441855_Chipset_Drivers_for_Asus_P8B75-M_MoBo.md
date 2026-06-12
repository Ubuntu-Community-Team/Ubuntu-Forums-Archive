---
title: "Chipset Drivers for Asus P8B75-M MoBo"
date: 2020-04-27
forum: Hardware
---

### Post by pscottbaker on 2020-04-27
I've been deploying Ubuntu on an Asus P8B75-M mobo with an Intel i7 proc with a Hauppauge WinTV-quadHD TV Tuner.

It looks like Ubuntu isn't detecting the tuner since I've followed the steps at the Hauppauge website add support for the tuner.
[https://www.hauppauge.com/pages/support/support_linux.html?#tabs-5](https://www.hauppauge.com/pages/support/support_linux.html?#tabs-5) 

The board has a couple of PCIe slots and I've tried them both with no luck.

I've installed Win7 and Win10 and both detect the card without installing chipset drivers so I know it works.

I've tried Ubuntu 16x and 18x, I also tried using Ubuntu 18 with the 4.15 kernel with no success.

All on-board peripherals are detected - NIC, sound, graphics

This has led me down the path to considering chipset drivers as a potential problem.

Any suggestions on chipset or other recommendations as to what my be preventing the tuner card from being detected would be appreciated.

---

### Post by CelticWarrior on 2020-04-27
Welcome.

> **pscottbaker said:**
> It looks like Ubuntu isn't detecting the tuner since I've followed the steps at the Hauppauge website add support for the tuner.
[https://www.hauppauge.com/pages/support/support_linux.html?#tabs-5](https://www.hauppauge.com/pages/support/support_linux.html?#tabs-5) 


Please post your actual Ubuntu release/version and exactly what you tried.

---

### Post by Yellow Pasque on 2020-04-28
> **pscottbaker said:**
> This has led me down the path to considering chipset drivers as a potential problem.

The Intel B75 chipset has been supported in the Linux kernel for some time. This isn't Windows where you need to hunt down your own drivers..

---

