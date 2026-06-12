---
title: "Hard drive clone to external hard drive"
date: 2008-08-25
forum: Hardware
---

### Post by Deadmode on 2008-08-25
Hi, I'm attempting to use HDDClone to clone my laptop hard drive to an external hd of a slightly smaller size.  The external is approximately 20gb smaller, however the original hd hardly has any space taken up at all.  I want to easily clone this over, but I'm having problems when I use HDDClone and Clonezilla.  HDDClone errors out and Clonezilla will not recognize the external HD. Can anyone help me out with my predicament?

---

### Post by phidia on 2008-08-25
You could you the commandline > dd see man dd. That will allow you to copy a partition from your internal to external HD. A useage example would be >  dd if=/dev/hda1 of=/dev/hdb1.

---

### Post by Deadmode on 2008-08-27
I will probably need to do using live cd?

---

