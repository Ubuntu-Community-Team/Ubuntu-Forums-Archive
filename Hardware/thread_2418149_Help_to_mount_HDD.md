---
title: "Help to mount HDD"
date: 2019-05-02
forum: Hardware
---

### Post by jpfinal on 2019-05-02
Hi, i'm new here and i need some help with this.
I have an SSD 250 GB with Windows 10 (partition C) along ubuntu 18.04; and another disk HDD 3 TB (partition D data).
My problem is in Ubuntu, from the SSD i can mount particion C of Windows, but i can't see the HDD disk.
Can you help me?

---

### Post by TheFu on 2019-05-02
Please post both 
```
lsblk
sudo fdisk -l 
df -Th
```
output. Using code tags, like I've done. It is important for readability so the columns all line up correctly.

Beware that NTFS is slow without some special options at mount time.  GUI tools don't allow options to be added.
[https://askubuntu.com/questions/34731/howto-auto-mount-windows-partitions-using-etc-fstab](https://askubuntu.com/questions/34731/howto-auto-mount-windows-partitions-using-etc-fstab) is the way.

---

