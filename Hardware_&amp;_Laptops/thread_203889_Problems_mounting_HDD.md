---
title: "Problems mounting HDD"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by invalid06 on 2006-06-26
I'm running Ubuntu 6.06 Dapper, and I have a completely clear straight out of the box 160GB Maxtor ATA Hard drive, and i cant seem to get it to mount to save my life, could anyone possibly help?

---

### Post by frodon on 2006-06-26
Is your question "How to mount my drive" ?

If yes it depends of the filesystem but if you come from windows it should be FAT32 or NTFS, you will find there the needed instructions to mount your hdd : 
[http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

---

### Post by invalid06 on 2006-06-26
It's a hard drive that's never been used before, i JUST took it out of the box today around noon, it's never had an OS on it or anything.

---

### Post by frodon on 2006-06-26
Ok, you must create some partitions before being able to use it, i advice you to use gparted to do it, it's in the "system" tab or you can lauch it typing "gparted" in a terminal.

Feel free to ask for help if you have some doubts on how make your partitions.

---

