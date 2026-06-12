---
title: "Are 32-bit Linux kernels designed to access only 1GB of RAM by default?"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by chrisbloe on 2007-09-23
My question is best summed up by the following URL.

Does Ubuntu fall into the category of using only 1GB of RAM?

[http://www.neowin.net/index.php?act=view&id=42757](http://www.neowin.net/index.php?act=view&id=42757)

---

### Post by reckless2k2 on 2007-09-23
i didn't read the link but ubuntu has highmem support built right into the generic kernel to see up to 4gb. i imagine that was your question. i have 4gb and it's seen just fine.

your should be able to run

> free -m

and verify this. make sure your bios can see the memory then the os will.

---

### Post by arkara on 2007-09-23
nope ubuntu sees my 3gb on 32bit system
so
it has no prob
look:
32bit are to 4 gb of mem
and 64 bit are about up to some terra bytes

---

