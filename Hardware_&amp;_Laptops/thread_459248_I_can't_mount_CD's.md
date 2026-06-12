---
title: "I can't mount CD's"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by Sarkinare on 2007-05-30
I have had Ubuntu for a few months now and recently for some reason when I try to mount a CD it comes up with the error 
```
mount: can't open /etc/mtab for writing: Input/output error
```
can anyone offer any advice?

---

### Post by kidders on 2007-05-31
Hi there,

That's an odd one! What does **ls -l /etc/mtab** tell you?

Having thought about this for a while, the only things I can come up with that might cause this are either very unlikely, or would be otherwise evident (eg running out of disk space, or having too many open files). It's making me wonder whether the error message really means what it says!

Can you mount CDs yourself in a terminal?

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by Tilo on 2007-05-31
are you root? 

you need to be root to mount or unmount partitions / CDROMs.

type sudo in front of the mount or unmount command, e.g.:

   sudo mount /dev/cdrom /mnt/tmp

---

