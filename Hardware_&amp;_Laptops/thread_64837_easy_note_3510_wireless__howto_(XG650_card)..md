---
title: "easy note 3510 wireless  howto (XG650 card)."
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by suoko on 2005-09-12
Hi,

I solved my problems with wireless card by following instructions found at [http://www.burtonini.com/blog/computers/acx111-2005-05-26-12-00?showcomments=yes](http://www.burtonini.com/blog/computers/acx111-2005-05-26-12-00?showcomments=yes)

INSTRUCTIONS:
"Hoary comes with the acx_pci module builtin, and a collection of firmware. However, the module will try and load TIACX111.BIN to the card, which is wrong. It will successfully load, but the card won't work. The trick on Hoary is to steal FwRad16.bin from the driver CD and put it in /lib/hotplug/firmware, and then delete TIACX111.BIN from the same location. Only then will the right firmware be uploaded."

---

