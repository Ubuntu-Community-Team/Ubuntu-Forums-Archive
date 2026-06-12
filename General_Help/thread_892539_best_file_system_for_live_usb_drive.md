---
title: "best file system for live usb drive?"
date: 2008-08-17
forum: General Help
---

### Post by chenlevy on 2008-08-17
Hi, all.

I read the HOWTOs on [Pen Drive Linux]("http://www.pendrivelinux.com/?"), and I wander if the ext2/3 and fat16/32 are the best options for live GNU/Linux USB flash drive installation.

I was Googleing and found out that:

1. There are several file systems designed for Flash drives such as: YAFFS, JFFS2 and LogFS. Among other things they provide wear-leveling and compression.

2. Some other file systems such as unionfs can combine the benefits of read only files systems such as squashfs with read/write file systems.

Here are some links I found:
* [Wikipedia: List of file systems -- Flash memory & solid state media file systems]("http://en.wikipedia.org/wiki/List_of_file_systems#Flash_memory_.2F_solid_state_media_file_systems")
* [The LogFS wiki]("http://www.logfs.org/logfs/")
* [JFFS2]("http://sourceware.org/jffs2/")
* [YAFFS]("http://en.wikipedia.org/wiki/YAFFS")

My Question: What is the best file system schema for a USB flash drive installation? Is there a Ubuntu remix for UBS flash drive installation, perhaps based on the [Netbooks remix]("http://www.canonical.com/netbooks") that uses such a schema?

---

### Post by irate.turtle on 2009-11-28
any answers?

---

### Post by Bjalf on 2009-11-28
> **chenlevy said:**
> 1. There are several file systems designed for Flash drives such as: YAFFS, JFFS2 and LogFS. Among other things they provide wear-leveling and compression.

Isn't the wear-leveling done in hardware on USB sticks? Would not hardware (controller) and software wear-levelling clash with each other?

I'd go with ext2 and possibly squashfs in case of space issues.

---

### Post by KayakJim on 2009-11-28
FAT32 is probably the best choice as it can be read by any OS by default.

---

