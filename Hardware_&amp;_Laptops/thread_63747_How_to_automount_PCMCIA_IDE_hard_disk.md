---
title: "How to automount PCMCIA IDE hard disk?"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by seanf on 2005-09-08
I've got a 260MB PCMCIA hard disk that I would like to mount automatically when it is inserted in the PCMCIA slot. Currently, I mount it manually with the following command:

```
mount -t vfat /dev/hde1 /mnt/ide
```

What do I need to do to have the disk automount when I insert it?

I tried uncommenting the samples in /etc/pcmcia/ide.opts and setting them to the appropriate values, but it didn't have any effect.

---

### Post by ianpeters on 2005-09-18
Yeah, I'd also be interested in an answer to this problem.

---

