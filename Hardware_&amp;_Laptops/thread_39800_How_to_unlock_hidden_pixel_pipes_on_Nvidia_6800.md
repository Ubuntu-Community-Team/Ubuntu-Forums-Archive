---
title: "How to unlock hidden pixel pipes on Nvidia 6800?"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by meldroc on 2005-06-06
I'm running Kubuntu Hoary on a system with an NVidia 6800 video card.  Just for background information, the low end 6800's (at least the AGP versions, PCI-E versions have a new chip that can't do this) use the same chipset as the 6800GT and 6800 Ultra.  The GT and Ultra have 16 pixel pipes and 6 vertex pipes.  The low end 6800 has only 12 pixel pipes and 5 vertex pipes, or does it?  Hmmm.

It turns out that in Windows, you can use a tool called Rivatuner to softmod the 6800 to reenable those hidden pixel and vertex pipelines, giving a very nice performance boost and ruining Nvidia's business model.  :grin: Of course, you do run the risk of graphics artifacts and crashes, because those hidden pixel and vertex pipes might be defective (hence the reason why this particular chip was sold as a 6800, not a 6800GT or 6800 Ultra.  Then again, maybe they had too many GT's and Ultras and not enough low ends, so they gave you a perfectly good chip.)  As for me, when I tried it in Windows, it worked great.  YMMV, just like overclocking.

Is there a way to unlock those pipelines in Linux?  I like having that extra performance boost.

---

### Post by voidlogic on 2005-06-06
I have been thinking about the same thing myself. Is Rivatuner opensource, I would be willing to port some of it to linux. Btw, on a similar note, if you like to overclock under linux, check this out- [http://www.phoronix.com/scan.php?page=article&item=197&num=1](http://www.phoronix.com/scan.php?page=article&item=197&num=1)

---

### Post by meldroc on 2005-06-08
Bump. ;)

---

