---
title: "sharing internal hard drive with unbuntu and windows"
date: 2008-11-29
forum: General Help
---

### Post by rob40001 on 2008-11-29
Hi i have 3 separate internal hard drives one with vista one with XP and one with ubuntu but I want windows to see my ubuntu hard drive so I can store files on it and vice versa is this possible? I believe if I formatted the drive to FAT32 I could do this although it is a 320gb hard disk so would lose a lot of space. Can a set up a sharing folder?

---

### Post by Wartender on 2008-11-29
yeah you can use gparted to make a fat32 partition (without formatting the entire hard drive) and windows will be able to read it and you can mount it in ubuntu, that's what i do.

---

### Post by Dalston on 2008-11-29
You can format it as a NTFS that way you can share bigger files.  Thats what I do.

---

### Post by Dalston on 2008-11-29
I should of added that you need to get ntfsprogs from the synaptic package manager so that gparted can format to NTFS.

---

