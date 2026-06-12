---
title: "Swapping Hard Drive to New Laptop"
date: 2008-11-14
forum: Hardware
---

### Post by undoIT on 2008-11-14
I have a few extra hard drives lying around. I was thinking it would be useful to install Ubuntu and a couple other distros on one of the drives for testing. If a friend wants to use Linux, it would be easier to test if I could just swap in the fully installed, fully updated hard drive. Is this possible?

I imagine the xorg.conf file might be problematic. Are specific drivers installed for the computer that is initally being installed to?

---

### Post by prshah on 2008-11-14
> **undoIT said:**
> easier to test if I could just swap in the fully installed, fully updated hard drive. Is this possible?


Yes, very possible. However, just to be on the safe side, in your "testing" versions, keep the graphics driver VESA; that will work with any graphics card.

xorg.conf is now marginalized from Hardy onwards, and may be completely discarded from the next version onwards. The current version respects settings in xorg.conf, but can work without it as well.

---

### Post by razy60 on 2008-11-14
i found these links when i was looking into doing something similar
 [http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)
 [http://www.ibm.com/developerworks/linux/library/l-fireboot.html?ca=dgr-lnxw09FireBoot](http://www.ibm.com/developerworks/linux/library/l-fireboot.html?ca=dgr-lnxw09FireBoot)
 main thing is is to install grub on the external device, otherwise the other pc wont see the ubuntu os and wont be able to load it.

---

