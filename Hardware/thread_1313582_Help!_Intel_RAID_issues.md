---
title: "Help! Intel RAID issues"
date: 2009-11-03
forum: Hardware
---

### Post by voltboyee on 2009-11-03
Hoping someone can help...

Here is my setup:

4x Western Digital 1TB drives
 - 200GB RAID 0 (Windows 7 and Apps / Games)
 - 1.8TB RAID 10 (Data)

Both arrays use all 4 disks.

Ubuntu has its own 80GB drive (/dev/sde). 

Install went fine and can boot into Ubuntu. However, the install seems to have hosed my RAID setup. In POST, Intel matrix thing says that my RAID 0 array has failed and the raid 10 is degraded. Seems like it thinks that the first disk is missing.

What I think has happened is that the install routine wrote to the MBR on the first disk without doing the software RAID stuff. This has cause the whole thing to go out of whack.

However, inside Ubuntu I can mount my 2 RAID drives and even write to them so no data has been lost.

I can't boot into Windows anymore tho.

Please could someone help? What do I do? Don't wanna have to reinstall Windows :P

---

### Post by voltboyee on 2009-11-03
Bump... still stuck. Any ideas?

---

