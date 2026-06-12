---
title: "usb disk - cant mount"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by maikki on 2007-11-05
Hi folks

a few days ago I've just unplug my flash disk from computer without unmounting. now i have problem to mount it to any OS (not only linux so do windows). I tried to reformat that flash but it went wrong too. 

dmesg:

[17211475.580000] cramfs: wrong magic
[17211475.640000] VFS: Can't find ext3 filesystem on dev sda.
[17211475.640000] NTFS-fs warning (device sda): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17211475.640000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17211475.640000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17211475.640000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.
[17211475.644000] FAT: invalid media value (0x58)
[17211475.644000] VFS: Can't find a valid FAT filesystem on dev sda.

can anybody help me??

thanks

---

### Post by ddrichardson on 2007-11-05
Looks like it's been corrupted after unsafe removal. As long as you don't need the data back - try [this]("http://blog.lynxworks.eu/?p=6").

---

### Post by maikki on 2007-11-05
> **ddrichardson said:**
> Looks like it's been corrupted after unsafe removal. As long as you don't need the data back - try [this]("http://blog.lynxworks.eu/?p=6").

thanks so much it works.

---

### Post by ddrichardson on 2007-11-05
Cool, can you mark the thread as solved, there's a link in my signature.

---

