---
title: "What format should I use for External HD?"
date: 2008-05-02
forum: Hardware
---

### Post by Deived on 2008-05-02
I'll be picking up a new external hard drive (not sure which one yet).  I'll be using it with both an Ubuntu laptop and a WinXP laptop.
I'm looking for some tips with what to do when using it with both OS's.  I'm not sure which format I should use.  From what I know, WinXP can't read a Linux partition (except through network), and I've had problems messing with NTFS in Ubuntu (mainly permissions).  I haven't messed with NTFS in Hardy yet though so not sure if it's any better
Any way, what format should I use? or should I just partition it and have both?
Any suggestions?

---

### Post by tech9 on 2008-05-02
> **Deived said:**
> I'll be picking up a new external hard drive (not sure which one yet).  I'll be using it with both an Ubuntu laptop and a WinXP laptop.
I'm looking for some tips with what to do when using it with both OS's.  I'm not sure which format I should use.  From what I know, WinXP can't read a Linux partition (except through network), and I've had problems messing with NTFS in Ubuntu (mainly permissions).  I haven't messed with NTFS in Hardy yet though so not sure if it's any better
Any way, what format should I use? or should I just partition it and have both?
Any suggestions?

use vfat...

example

```
$ sudo mkfs.vfat /dev/sda1
```

---

### Post by starcannon on 2008-05-02
Tech9 is right on the money, that should work perfectly.

---

### Post by Deived on 2008-05-02
> **tech9 said:**
> use vfat...

example

```
$ sudo mkfs.vfat /dev/sda1
```

VFAT? isn't that like FAT32?  Isn't there a problem with FAT32 and files larger than like 2GB (or some other number)?  There will definitely be large file sizes involved.

---

### Post by tech9 on 2008-05-02
> **Deived said:**
> VFAT? isn't that like FAT32?  Isn't there a problem with FAT32 and files larger than like 2GB (or some other number)?  There will definitely be large file sizes involved.

not at all...

the size problem that you are referring to - is windows fat32 (don't you just love Microsoft :-& )

vfat -  is a format that will support both your linux files and your windows files

---

### Post by Deived on 2008-05-02
> **tech9 said:**
> not at all...

the size problem that you are referring to - is windows fat32 (don't you just love Microsoft :-& )

vfat -  is a format that will support both your linux files and your windows files

Ah OK.  So, for clarification...
Formatting a drive as FAT32 in Windows makes it a Windows FAT32, which works in both OS's but suffers from the large file size problem.
Formatting a drive as vfat in Linux makes it a FAT32 that will work in both OS's, but does NOT suffer from a problem with large file sizes when using it with either OS.

Is this correct?

---

### Post by tech9 on 2008-05-02
> **Deived said:**
> Ah OK.  So, for clarification...
Formatting a drive as FAT32 in Windows makes it a Windows FAT32, which works in both OS's but suffers from the large file size problem.
Formatting a drive as vfat in Linux makes it a FAT32 that will work in both OS's, but does NOT suffer from a problem with large file sizes when using it with either OS.

Is this correct?


that is correct :)

---

