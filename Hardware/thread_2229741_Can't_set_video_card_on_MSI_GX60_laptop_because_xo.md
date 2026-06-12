---
title: "Can't set video card on MSI GX60 laptop because xorg.conf reverts on reboot"
date: 2014-06-15
forum: Hardware
---

### Post by Retro Banana on 2014-06-15
I recently purchased a new MSI GX60 laptop, and immediately installed Ubuntu 14.04, 64-bit on it. It has two graphics cards, an ATI Radeon 8650 (which is integrated with the CPU) and an ATI Radeon 8970, the discrete graphics card. After installing the "fglrx" package, I rebooted. Then I used "sudo aticonfig --adapter=1 --initial", which set the default video card to the discrete one. A simple "cat /etc/X11/xorg.conf" confirmed that it worked. But after rebooting, the xorg.conf was back to the default file! Why is xorg.conf reverting after a reboot?

---

