---
title: "Issue with external hdd - compatibility"
date: 2020-11-06
forum: Hardware
---

### Post by AnupamMitra on 2020-11-06
I have voluminous documents (Libre Office, Words & PDF) in my Ubuntu PC. For safety, recently I have taken backup of all these documents in my external HDD (Seagate 2 TB). For backup, I use Grsync. Now sometimes it become necessary to go through the documents in Windows PC. But this External HDD is not shown in Windows 10. Would it not be possible to read these documents in Windows PC?

---

### Post by CelticWarrior on 2020-11-06
It depends on the file system.

FAT, NTFS or exFAT are supported by Windows (as well as Linux).
EXTn, ZFS, BTRFS, etc., the file systems typically used in Linux aren't supported by Windows.

---

### Post by mastablasta on 2020-11-06
how is it formatted? if it's ext4 you can use ext2fsd to read: [https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

---

### Post by AnupamMitra on 2020-11-06
> **CelticWarrior said:**
> It depends on the file system.

FAT, NTFS or exFAT are supported by Windows (as well as Linux).
EXTn, ZFS, BTRFS, etc., the file systems typically used in Linux aren't supported by Windows.

Thanks for your reply. The file system of my external HDD is ext4.

---

### Post by AnupamMitra on 2020-11-08
> **mastablasta said:**
> how is it formatted? if it's ext4 you can use ext2fsd to read: [https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

Thanks for your reply. As suggested, I gone through the link and installed Ext2Fsd. Voila, now I can see not only my External HDD but also the entire linux partitions from Windows 10. Thanks a lot.

---

