---
title: "How to remove GPT Protective Partition after unmounting Samba drive?"
date: 2018-06-15
forum: Hardware
---

### Post by evoconian on 2018-06-15
After I unmount an HDD from my server that was being used in a Samba share, I cannot access it in my windows computer due to a GPT Protective Partition.

Is there any way that I can remove this protection in Ubuntu without totally formatting the drive?

It is formatted in NTFS.

---

### Post by oldfred on 2018-06-17
Not sure what partition you are discussing?
Windows reads gpt just fine, since Windows 7.

Post this for that drive:
sudo parted -l

---

