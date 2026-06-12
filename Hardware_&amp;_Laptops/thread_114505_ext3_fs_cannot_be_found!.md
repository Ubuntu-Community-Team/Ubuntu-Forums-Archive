---
title: "ext3 fs cannot be found!"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by tUrtleAE86 on 2006-01-08
I've got one huge problem. It's my fault, I was really stupid.

Anyways I hit ctrl-c during an e2fsck on my secondary hard drive (with an EXT3 fs), while it was going through a huge list of prompts. And now, I can't access the disk at all.

There is no /dev/hdb1 anymore, only /dev/hdb.
So, as a result, I cannot do an "e2fsck /dev/hdb1".

I have almost 200GB of data on this drive, and, well, I can't afford to lose it.

Is there anyway of fixing this problem? I'm getting really desperate here. :(

---

