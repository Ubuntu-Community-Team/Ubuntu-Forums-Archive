---
title: "Can I change what kernel driver a device should load?"
date: 2017-06-18
forum: Hardware
---

### Post by redking3 on 2017-06-18
I am trying to get my usb-controller to boot with vfio-pci driver so I can pass it away to a VM.
Problem is it keep loading with the default driver: xhci_hcd

I solved a similar issue with my Nvidia GPU, but there I could simply block the driver from loading at boot and everything work as I wanted it to, but this will not work in this case because my on-board usb controllers use the same driver.. 

So if possible I need to somehow block that specific device from using its default driver so it will load with the alternative vfio driver.

Anyone got experience with similar issues?

---

### Post by gsahli on 2017-06-20
I'd suggest you try the blacklist > install workaround from here:
[https://wiki.archlinux.org/index.php/Kernel_modules#Blacklisting](https://wiki.archlinux.org/index.php/Kernel_modules#Blacklisting)

PS - make sure no other modules "depend" on the one you kill - use lsmod

---

