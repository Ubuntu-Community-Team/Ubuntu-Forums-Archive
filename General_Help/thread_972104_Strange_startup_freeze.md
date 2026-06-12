---
title: "Strange startup freeze"
date: 2008-11-05
forum: General Help
---

### Post by Trogdorn on 2008-11-05
I have recently installed 8.10 on a HP laptop and experienced a freeze during the initial install process and every subsequent startup. The bar starts to move and then stops. I checked the install disk and ran a mem test and both were fine
Here's what's strange, if I hit any key the bar moves just a little, repeated key strokes moves it along a tad and it will eventually start OR just hit the power on button for the laptop once and it finishes starting just fine.
I removed the splash screen to see where it stops and here is the last line:
ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000

Since it's my wife's machine and I gave Linux such a big build up it would be great to fix this glitch for her. Thanks for any help, these forums are the best!

---

### Post by SoCalChris on 2008-11-05
This is a bug in the 2.6.27 kernel that seems to affect mostly HP laptops. I've personally seen it in 8.10 since it was in alpha, and in the Fedora 10 Beta.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247)

---

### Post by Trogdorn on 2008-11-06
Thanks for the reply pointing to the known bug issue. At least I don't feel like the Lone Ranger now... here's hoping for a fix soon.

---

