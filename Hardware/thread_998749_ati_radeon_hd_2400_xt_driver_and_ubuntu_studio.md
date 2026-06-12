---
title: "ati radeon hd 2400 xt driver and ubuntu studio"
date: 2008-12-01
forum: Hardware
---

### Post by Pax08 on 2008-12-01
Does anybody have experience which driver to use, the one ubuntu suggests (8.4?) or the one from ATI web site (8.11)?

---

### Post by markbuntu on 2008-12-02
If that is an AGP card, the ubuntu driver will not work.

If you use the one from ati, you may have problems with future kernel updates, especially with the rt kernel in UbuntuStudio. 

Just remember to keep the download so you can install it again and to turn off any desktop visual effects when you see you are going to get a kernel update just in case the kernel modules do not get loaded which can happen and will give you a white screen if compiz (desktop visual effects) is running.

That said, the 8.11 driver is much improved from 8.4 but some people are reporting problems with it. The 8.10 driver may be a better choice.

---

