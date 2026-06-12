---
title: "Installing ATI/AMD proprietary FGLRX graphics driver offline on Ubuntu 8.10"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by Gilbert2 on 2009-01-16
I just installed Ubuntu 8.10 on a PC with an ASUS Radeon 9600SE graphics card but no Internet. If I go to System > Administration > Hardware Drivers, a Hardware Drivers window appears indicating that the ATI/AMD proprietary FGLRX graphics driver is not activated. If I click Activate, then enter my password, it simply returns to the Hardware Drivers window, apparently because there is no Internet connection.

How do I go about installing this driver offline? Also, how do I uninstall it afterwards and return to the previous drivers if I decide I don't like them for whatever reason? Any help is greatly appreciated. Thanks.

---

### Post by Gilbert2 on 2009-01-29
Never mind, I eventually figured it out. By the way, I forgot to mention that the machine's architecture is i386. Anyway, for the curious:

1. On a PC that does have Internet, I downloaded the following from packages.ubuntu.com:
  - dkms_2.0.20.4-0ubuntu2_all.deb
  - fglrx-kernel-source_8.543-0ubuntu4_i386.deb
  - xorg-driver-fglrx_8.543-0ubuntu4_i386.deb
2. I installed each of them from a terminal window (in the order listed above) using 'sudo dpkg -i <package_name>.deb'
3. I went into System > Administration > Hardware drivers. With "ATI/AMD proprietary FGLRX graphics driver" highlighted, I clicked Activate & entered my password.
4. Rebooted.
5. Initially, the display was a bit wacky. I couldn't see the top menu bar (or whatever it's called) in order to change my resolution. I vaguely remembered that ctrl-alt-minus (or plus) could change the resolution, so I tried that. I finally saw the top menu bar and switched to the resolution I wanted via the menus.

And that was it! The new driver seems to be working perfectly fine. The hardest part was determining what packages to get.

---

### Post by jpope on 2009-02-05
Thanks.
I had the same issue before finding this post. Worked perfectly with my Acer Aspire.

---

