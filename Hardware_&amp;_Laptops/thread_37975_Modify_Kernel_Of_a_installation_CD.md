---
title: "Modify Kernel Of a installation CD?"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by zootreeves on 2005-05-29
Hi,

I am trying to install linux from a usb hard drive and I think i'm nearly there. But there is one major problem.

When i boot the kernel from the installation cd using my usb hard drive Ig get a n error

kernel painc -not syncing: VFS: Unable to mount root...

I know this is becuase the kernel is not loading modules to support the usb device so how can I modify the kernel to load:

sd_mod
ehci-hcd
uhci-hcd
ohci-hcd
usb-storage

---

