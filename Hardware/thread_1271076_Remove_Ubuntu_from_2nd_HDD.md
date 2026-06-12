---
title: "Remove Ubuntu from 2nd HDD"
date: 2009-09-20
forum: Hardware
---

### Post by elgatonl on 2009-09-20
Hi,

I have 2 physical HDDs on my computer, one with XP and one with Ubuntu. I'm using dual boot but there are no partitions.

I cannot see the Ubuntu drive when I am booted into XP, but it is visible in the BIOS.

I have installed Ubuntu on my MacBook and now I want to re-format the Ubuntu drive on my PC so that XP can see it and use it for extra storage.

Can anyone help me out here?

thanks,

Mark

---

### Post by SlugSlug on 2009-09-20
> **elgatonl said:**
> Hi,

I have 2 physical HDDs on my computer, one with XP and one with Ubuntu. I'm using dual boot but there are no partitions.

I cannot see the Ubuntu drive when I am booted into XP, but it is visible in the BIOS.

I have installed Ubuntu on my MacBook and now I want to re-format the Ubuntu drive on my PC so that XP can see it and use it for extra storage.

Can anyone help me out here?

thanks,

Mark


in XP ...  right click my computer > manage > disk managment#

you should see it there and you'll be able to format etc

---

### Post by pastalavista on 2009-09-20
Boot-up the live CD and use GParted (System > Administration > Partition Editor) to delete Ubuntu and format the drive as NTFS. If you don't want to delete Ubuntu but just enable Windows to see and use the drive, you'll need to install software so Windows can handle ext2/3 file systems. [DiskInternals]("http://www.diskinternals.com/linux-reader/") makes a free program that my son says works great.

---

### Post by elgatonl on 2009-09-20
Thanks SlugSlug,

worked like a charm, fast and easy.

---

