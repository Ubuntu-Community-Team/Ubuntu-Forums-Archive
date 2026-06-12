---
title: "How to understand bootchart to fix slow boot?"
date: 2012-08-14
forum: Hardware
---

### Post by twengg on 2012-08-14
Hi all! I have bootchart installed and the charts show up, but I don't know how to read them. I don't know what shouldn't be there, or what's taking too long. 
Maybe someone could help me decipher my bootchart, or even post an Ubuntu 11.10 bootchart booting in less than 30 secs (not ssd, please) so I can compare.

[http://postimage.org/image/y5as1cfrj/](http://postimage.org/image/y5as1cfrj/)

---

### Post by SlugSlug on 2012-08-14
is 55 seconds long for a Celeron CPU?

It did do a filesystem check on that boot (fsck.ext4)

---

### Post by twengg on 2012-08-16
Thanks slugslug for your reply. So 55 secs is normal for my cpu? And should I run a manual fsck to prevent fsck on boot?

---

### Post by SlugSlug on 2012-08-16
I'd say so..

as for fsck it's done automatically every X amount of reboots - I wouldn't worry about it

---

