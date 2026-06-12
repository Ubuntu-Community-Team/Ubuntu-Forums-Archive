---
title: "&quot;no journal&quot; kernel msg for ext2 part."
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by thePythonAlchemist on 2005-04-10
During bootup I get a message that shows up in the kernel log:

```
ext3: No journal on filesystem on hda1
``` 

But hda1 is a ext2 partition. I know that they're essentially the same thing, except that ext3 has journalling capabilities; but still, I don't know why there would be a message about a journal being on an ext2 partition. Both fstab and mtab show that the part is mounted as ext2. So, is this message indicative of a problem? Thanks in advance.

---

