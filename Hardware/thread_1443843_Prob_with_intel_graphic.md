---
title: "Prob with intel graphic"
date: 2010-04-01
forum: Hardware
---

### Post by Mark Phelps on 2010-04-01
The Xorg.conf file clearly indicates that you're using an ATI video chipset, not Intel.  So, what makes you believe that you're using an Intel video chipset?

You can't have two video drivers installed at the same time.  You will need to figure out which one is the correct one.

To get an idea, open a terminal and enter "sudo lspci".  Down near the bottom of the output list, you should see an entry for your video chipset.  That will tell you what chipset you're really using.

---

### Post by coffeecat on 2010-04-02
Yes, you've got an Intel graphics chipset. So, why were you using an xorg.conf for an ATI card? Perhaps that's your problem. The Intel graphics driver is included in a default install.

---

