---
title: "Reformatted my external USB drive, now it won't automount."
date: 2008-06-19
forum: Hardware
---

### Post by petzworld999 on 2008-06-19
I recently decided that I didn't need all my stuff on my external hard drive, so I reformatted it. Now it won't automount. I did it with fdisk and mkfs.vfat, using the fat32 file system. It mounts manually, but not automatically. Any help would be appreciated.

---

### Post by Nikitas350 on 2008-06-19
Did you formatted in ntfs? I had some problems with my usb flash drive (which was in ntfs) when i disconnected not "safely". Try to mount it one time in a windows machine and remember to remove it safely...

---

### Post by petzworld999 on 2008-06-19
Nope, I formatted it as FAT32. It shows up in fdisk -l and gparted as FAT32.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
To mount anything automatically you need to edit /etc/fstab

---

