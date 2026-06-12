---
title: "2nd hard drive unaccessable"
date: 2005-11-19
forum: Hardware &amp; Laptops
---

### Post by HokeyFry on 2005-11-19
i have two hard drives in my computer, and only the one that Ubuntu is installed on is available for using after I boot up. There are two partitions on it -- an 'ext3' and a 'swap'. If someone could help me, that would be great.

---

### Post by kruz on 2005-11-19
sudo mkdir /secondhd

sudo mount /dev/hdb1 /secondhd

where hd=hardrive
b=hard drive 2
1= partition to mount
:D

---

### Post by HokeyFry on 2005-11-19
how do I make it automount?

---

