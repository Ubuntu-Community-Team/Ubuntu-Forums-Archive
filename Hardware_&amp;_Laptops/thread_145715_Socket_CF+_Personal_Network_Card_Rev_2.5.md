---
title: "Socket CF+ Personal Network Card Rev 2.5"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by wulvyrn on 2006-03-16
I'm trying to get this working with the dtl1_cs module it's not built in to the /etc/pcmcia/config nor does there appear to be a kernel one for it.

is this card supported?

Socket 0:
  product info: "Socket", "CF+ Personal Network Card Rev 2.5"
  manfid: 0x0104, 0x0096
  function: 2 (serial)

---

### Post by wulvyrn on 2006-08-22
i've tried this with dapper and there is no dtl1_cs driver loading for the card.

I'm still trying to get rev. F or H working.

If someone can point me to a bluetooth pcmcia or cf card that works with dapper out of the box, i'd love to get my bluetooth mouse to work with my laptop!

---

### Post by wulvyrn on 2006-08-24
I found this post closed in the developers forum.  Is this fixed in the kernel?  thanks.

======================================
Hello everyone,

I have a Toshiba laptop, and have been using Socket's CF bluetooth adapter with a cf-to-pcmcia adapter. It's a great bluetooth card - it does not protrude from the computer, uses minimal power, has great range. Here is my problem: it does not work out of the box in Ubuntu. I googled the card and discovered how to patch 8250.c in the linux sources, and then compile my own kernel; when this is done, an hciattach command makes the adapter fully useable. However, I would really like to keep the official Ubuntu kernel because it works really well for me in all other respects.

Is it possible to somehow patch the official kernel, or create a serial module with the patched 8250.c?

If anyone wants the patch for 8250.c, just let me know.

Thanks!
================================
from Roner

---

