---
title: "Can't eject from DVD drive after upgrade to Hoary"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by cuoog on 2005-04-09
OK, just upgraded to hoary via apt-get, everything seemingly went smoothly until:

1) media playback is much choppier than before.

2) media from the optical drive won't eject.  (these issues may be related, but this one is the more pressing of the two so I'm gonna try and solve this first).  this was not a problem in warty.

Here is the error I get when I try and eject a CD or DVD in hoary:

"eject: unable to eject, last error: Invalid argument"

yet, when i do a sudo eject it works fine.

Any thoughts?  How do I set eject permissions?

If it matters, it's a Lite-On 1633 burner and a SiS755 chipset with an athlon64 processor using the k7 kernel.

TIA,

db

---

### Post by soul_rebel on 2005-04-10
Check if you are in the CDROM group

---

