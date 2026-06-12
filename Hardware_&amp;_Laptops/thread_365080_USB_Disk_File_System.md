---
title: "USB Disk File System"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by ShareBuntu on 2007-02-19
Hi everyone,

I was wondering, is there a "preferred" usb disk file system when it comes to Linux? Currently, it's formatted as FAT32.

---

### Post by aa.ivanov on 2007-02-19
Moving the usb disk between different PCs. Some on linux, soe on windows you need a universal filesystem. I think FAT is the best option in terms of interoperability. As for linux itself - I don't think it'll object to any filesystem as long as it supports it.

---

### Post by ShareBuntu on 2007-02-19
> **aa.ivanov said:**
> Moving the usb disk between different PCs. Some on linux, soe on windows you need a universal filesystem. I think FAT is the best option in terms of interoperability. As for linux itself - I don't think it'll object to any filesystem as long as it supports it.

I'm only going to transfer files on Linux systems using this particular usb disk. I thought that perhaps there exists some type of "optimized for Linux" files sytem that'll offer a performance boost?

---

### Post by mcduck on 2007-02-19
> **'Ace[of]Bytes said:**
> I'm only going to transfer files on Linux systems using this particular usb disk. I thought that perhaps there exists some type of "optimized for Linux" files sytem that'll offer a performance boost?
If it's for Linux only you could use Ext2 (for flash disks) or Ext3 (for hard disks).

Ext2 for flash because flash drives have limited write cycles and journaling filesystems like Ext3 would reduce the lifetime of the device.

---

### Post by ShareBuntu on 2007-02-19
I formatted the usb disk to use the ext2 file system but it seems to be a lot slower than fat32.  Is this normal?

---

