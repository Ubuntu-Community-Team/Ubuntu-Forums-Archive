---
title: "keyboard fails - 2.6.12-9-686-smp"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by neouser99 on 2005-10-18
strange error here...

above is the kernel that i am running, and i have even tried to uninstall it and re-install it and the problem still exists. i am not to sure where to look for any errors, but /var/log/messages seems clean except for below. when i boot, i can't enter password, change terminals, or anything, but it does get all the way to the kdm login screen...which is weird. any help would be greatly apprectiated, the only thing that i can remember changing anywhere recently according to the kernel is install the fglrx drivers for my radeon 9800 pro gfxcard...

```
Oct 18 22:13:38 localhost kernel: [4294668.782000] PNP: PS/2 controller doesn't have AUX irq; using default 0xc
Oct 18 22:13:38 localhost kernel: [4294668.782000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 112
Oct 18 22:13:38 localhost kernel: [4294669.293000] pnp: Device 00:08 does not supported disabling.

```

EDIT: I have removed the fglrx drivers, and once again reinstalled the linux-image-686-smp which is currently 2.6.12...any one have any ideas?? it is really weird, and not random, every time it happens. The other strange thing is that sometimes if I move to the out screen or choose a different screen (using alt + f1 or whatever)... the keyboard will work, except for one or two keys which the kernel continually complains about.

-neo

---

