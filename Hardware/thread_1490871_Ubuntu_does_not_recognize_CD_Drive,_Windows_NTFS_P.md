---
title: "Ubuntu does not recognize CD Drive, Windows NTFS Partition, or USB Drives"
date: 2010-05-22
forum: Hardware
---

### Post by sauceytaco on 2010-05-22
Hello all,

I installed the Ubuntu 10.04 LTS w/ dual boot alongside Windows and Ubuntu will not recognize when I insert a CD, insert a USB flash, or look for my NTFS Windows partition in the "Computer" menu. None of the drives show up.

It's an old eMachines t6414 with the following additional hardware:

-NVidia 8500gt (ASUS)
-Buffalo WLI2 PCI G54 wireless card
-1 additional GB of Kingston DDR RAM

I'm not sure of the specific model of the CD drive, but since the issue affects USB, CD and the NTFS partition I think there's just some hardware setting that's screwed up.

Thanks in advance.

---

### Post by pytheas22 on 2010-05-23
That's strange.  What is the output of these commands:

```
mount
ls /dev | grep -e hd -e sd
```

---

