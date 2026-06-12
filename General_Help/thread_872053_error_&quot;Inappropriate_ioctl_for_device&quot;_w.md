---
title: "error &quot;Inappropriate ioctl for device&quot; when doing rar decompression"
date: 2008-07-27
forum: General Help
---

### Post by unicorn_2003_1 on 2008-07-27
So I was doing a decompression of a multipart rar file (like ***.part1.rar, ***.part2.rar, etc) on a Ubuntu 8.04 i386 installed from Wubi. 

In Nautilus, I rightclicked on one file, then "Extract here", the Archive Manger would report an error like "Inappropriate ioctl for device". However if I open the file and tell Archive Manager to extract to a directory under /host (the Windows part), it would be fine.

I don't know whether this is to do with that "extract here" script or the way Wubi mounts drivers or Ubuntu having disabled a certain DMA setting of the HD. Anyone has a solution or some suggestion to this? Thak.

---

### Post by ago on 2008-07-29
This is certainly not a wubi issue, you might want to check the general support forum for tips on how to perform the operation you want.

---

