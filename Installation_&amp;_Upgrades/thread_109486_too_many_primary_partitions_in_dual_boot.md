---
title: "too many primary partitions in dual boot"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by HarryMangurian on 2005-12-28
I successfully installed Breezy in a dual boot setup with Windows XP.

When I tried to backup my C: partition using Ghost, I got the following just before the Ghost process starts:
[http://www.pbase.com/nupbase/image/54084416.jpg]("http://www.pbase.com/nupbase/image/54084416.jpg")

When I use partition magic to examine my partition setup, I found FIVE (5 !) primary partitions as follows:
[http://www.pbase.com/nupbase/image/54084425.jpg]("http://www.pbase.com/nupbase/image/54084425.jpg")

(1) The first is a partition DELL puts on their systems to support diagnostics, etc.  I am afraid to make this non-primary - anyone know if that's safe ?
(2) The second is my Windows XP boot, which must be primary.
(3) The third is my Linux boot (must be a primary- right ??)
(4) My Linux swap (Partition Magic doesn't know what partition type it is and will not let me change it).
(5) "extended" partition.  I don't know what the heck it is, but based on size it is apparently the same space as my FAT32  G: partition (unless my disk grew !).

Any help greatly appreciated.  I really like Ghost and would like to be able to use it.

---

### Post by paddyg on 2005-12-28
An extented partition is a sort of container to extend the number of partitions beyond the usual 4 per HD.

I've always used extented linux partitions so I can have several mount points (/boot, root, /home, /var)

Strange PM doesn't know what swap is, as it seems to be listed in the types it can handle.

Sorry I can't be of any help with ghost

---

