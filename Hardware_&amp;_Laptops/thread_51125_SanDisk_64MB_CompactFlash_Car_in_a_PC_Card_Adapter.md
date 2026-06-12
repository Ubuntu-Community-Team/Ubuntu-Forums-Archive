---
title: "SanDisk 64MB CompactFlash Car in a PC Card Adapter not accessable"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by jdkron on 2005-07-22
When I insert the SanDisk 64MB CompactFlash Car which is in a PC Card Adapter into the card slot Ubuntu seems to recognize it because it shows up in the devise manager.

However, I do not get a desktop icon, it doesn't show up in the "places" menu, and not in "computer".

Any advice?

Thanks in advance

---

### Post by major on 2005-07-23
I also use a CF>PCMCIA adapter with memory cards. On my system, Ubuntu doesn't automount them.

If you type dmesg right after inserting the card you should see several lines about Probing IDE Interface...followed by the device name (mine gets added as hde).

---

### Post by jdkron on 2005-07-24
Thanks for responding!

I get hde as well. Now what?

How do I get a desk top icon so I can click and drag? How do I mount it?

Thanks again for taking the time - much appreciated!

---

