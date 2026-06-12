---
title: "boot stuck with fx 5500"
date: 2009-01-23
forum: Hardware
---

### Post by reformy on 2009-01-23
Hi all
I have a working machine with P4 3Ghz, 1.25GB memory and built-in simple video card. I've installed mythbuntu 8.10 as a front end on it, and it works OK.
Now i bought a better video card for it, GeForce fx 5500 (Forsa). When i plug it in and start the machine, i see the mythbuntu logo and the progress bar, but it gets stuck at about 10% and then I'm thrown from the X to a text screen with a lot of Segmentation Fault.

I've downloaded the drivers from nvidia but i don't have how to install it, if i try without the card it says "no card" and with the card i get stuck with no shell.
I've searched the forums and can't find a good explanation for this.

What can I do?
Thanks
Yair

---

### Post by HavocXphere on 2009-01-23
Try setting the driver in xorg.conf to "vesa". (/etc/X11/xorg.conf) Be sure to make a backup of xorg.conf & remember you need admin rights to change/save it.

---

### Post by reformy on 2009-01-25
> **HavocXphere said:**
> Try setting the driver in xorg.conf to "vesa". (/etc/X11/xorg.conf) Be sure to make a backup of xorg.conf & remember you need admin rights to change/save it.

Thanks.
Ive added the "vesa" driver, and it didnt work, still got thrown to text screen in the middle of the boot.
Is there a way to see the log in such a problem?
any other thing i can try?

thanks
yair

---

### Post by reformy on 2009-05-31
I've tried this card:
[http://www.amazon.com/EVGA-256-A8-N401-LR-e-GeForce-6200-Graphics/dp/B001U3YJRG/ref=sr_1_6?ie=UTF8&s=electronics&qid=1243789421&sr=8-6](http://www.amazon.com/EVGA-256-A8-N401-LR-e-GeForce-6200-Graphics/dp/B001U3YJRG/ref=sr_1_6?ie=UTF8&s=electronics&qid=1243789421&sr=8-6)
still - the boot is stuck in the middle (probably because of drivers).

Any idea on how to solve this?

---

