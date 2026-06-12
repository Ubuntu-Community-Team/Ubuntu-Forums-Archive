---
title: "external hard drive connected by USB"
date: 2008-05-15
forum: Hardware
---

### Post by scottbporter on 2008-05-15
Hi fellow ubuntuers,

how do I get my ubuntu system to mount/see my external hard drive which is connected via a USB cable. I know on windoze, it takes a bridge driver or something to that effect.

Thanks.

---

### Post by hermes0710 on 2008-05-16
Logicaly, the drive will be automounted upon insertion but if you want it to be mounted in a specific folder then you should enter a new entry in your fstab file. Notice that since it's an external driver, the entry should refer to it's uuid and not the /dev/??? entry. Just read the fstab guide if this is like greek to you :)

---

### Post by scottbporter on 2008-05-17
Thank you! I will give it a try when I get some time off from work.

---

