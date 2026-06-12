---
title: "Help - Adding memory etc...."
date: 2006-02-21
forum: Hardware &amp; Laptops
---

### Post by MJSOnline on 2006-02-21
Hi all.

Just a few questions.

If I add more memory to my system once Ubuntu is installed does the system pick that up and use it?  Does it reduce the usage of thge swap partion?  Does that also work with video cards, audio cards etc?

Thanks.  Matthew

---

### Post by bjweeks on 2006-02-21
> 
If I add more memory to my system once Ubuntu is installed does the system pick that up and use it?

Yes.

> Does it reduce the usage of thge swap partion?

Yes.

> Does that also work with video cards, audio cards etc?


Yes.

---

### Post by mjwood0 on 2006-02-21
Let's clarify a little here.

If you install memory and it is compatable with your system, the BIOS (on the motherboard) will recognize the memory and so will Ubuntu.  If the BIOS doens't see it, neither will Ubuntu.

More system memory will reduce the usage of the swap partition.  It's won't shrink the partition size, but you'll see it used less.  Swap is generally only used when your RAM is almost used up.

Installing new hardware is generally quite easy so long as you ensure that the hardware you install is Linux compatable.  Also, just plugging in new video cards may not make things work quite right.  You'll still have to install the correct drivers, and make sure your window manager is properly configured.

If you have any questions, ask here first and someone will probably have done something similar.

---

