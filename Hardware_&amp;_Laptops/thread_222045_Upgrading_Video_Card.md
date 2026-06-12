---
title: "Upgrading Video Card"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by binarymelon on 2006-07-24
I'm going to be making a very small upgrade for my video card.  I'm going from the FX5200 to the 6200.  This is mainly for better DVI support.  Will I need to make any changes to my setup, re-install nvidia drivers, change xorg.conf or anything of the sort when I do this?

---

### Post by hw-tph on 2006-07-26
If you haven't messed about with your Device section in your xorg.conf you shouldn't have to change a single thing. I have done similar upgrades without changing anything and while it works as expected, the Device Identifier string in xorg.conf might be a little confusing (being set to whatever card was in the machine when Ubuntu was originally installed) but it doesn't affect the function of anything.


Håkan

---

