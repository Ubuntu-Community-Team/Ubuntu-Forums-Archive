---
title: "external hard drive support"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by chazn85 on 2007-06-23
Hi all,
Pretty new to ubuntu but loving it so far!!!  So much better than windows.  However one thing has me stumped at present.  I have an external USB drive which i can copy things off off but dont seem to be able to copy things to.  I reckon this is because it seems to be read only.  Will i need to install some sort of ntfs program for inux (ntfsprogs??).  My linux partitions are ext3 if that helps.

Thanks in advance

---

### Post by taurus on 2007-06-23
If your external harddrive is ntfs, then you need to use ntfs-3g driver to write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by chazn85 on 2007-06-23
thanks that worked i tried the automatic way before.  That didnt work!!!  Will this be detected in vmware as well?

Thanks

---

