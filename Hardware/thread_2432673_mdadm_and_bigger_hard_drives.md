---
title: "mdadm and bigger hard drives"
date: 2019-12-06
forum: Hardware
---

### Post by halfnote6 on 2019-12-06
If I wanted to replace, say, about 7 or 8 6TB SAS hard drives in an mdadm RAID6 array with 12TB ones, I am given to understand that I can simply swap them out one by one and then expand the partition size.

Anyone have a quick reference on how to do this? I've been skimming the mdadm documentation and I'm not finding anything exactly like what I'm looking for. 

Many thanks, in advance! = )

---

### Post by SeijiSensei on 2019-12-06
I think you want to use the "grow" parameter to mdadm, but I've not done that myself.

[https://raid.wiki.kernel.org/index.php/Growing](https://raid.wiki.kernel.org/index.php/Growing)

---

### Post by rsteinmetz70112 on 2019-12-09
I have done it although not with such large drives. It works as advertised. If you have enough Hard Drive connections you can simply add the new drive to the array and then remove the old drive or you can "fail" the drive you want to replace, remove it then add the new drive and sync it up. It works pretty much like replacing a bad drive in an array.

---

