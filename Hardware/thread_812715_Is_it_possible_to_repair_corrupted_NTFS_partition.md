---
title: "Is it possible to repair corrupted NTFS partition?"
date: 2008-05-30
forum: Hardware
---

### Post by Kuniva on 2008-05-30
I was messing around with some MBR repairing tools. I found [ms-sys]("http://ubuntuforums.org/showthread.php?t=616540#2") and I followed linked instructions. It didnt't quite work as expected. It suggested I force writing of boot-loader to sda1 (my Windows partition). Ignoring the warning I did it. It seams it corrupted start of my Windows partition. Now I get "Invalid partition table" and no paritioning software seams to be able to read what format partition is and what is it's size. I know its NTFS and 90GB. Is there any way I can reapir corrupted filesystem? Or at least save some data off it?

Thanks in advance.

---

### Post by bigken on 2008-05-30
yep run the xp cd go to repair console run fixmbr & fixboot

---

### Post by Kuniva on 2008-05-30
> **bigken said:**
> yep run the xp cd go to repair console run fixmbr & fixboot

What if you don't have your original recovery CD? Can you use someone else's? Or does it check for CD-Key? And what if you don't know password for your Windows? This system came with pre-installed OEM XP and im not sure what password is.

---

### Post by bigken on 2008-05-30
yes use any cd

it might not have a password

---

### Post by Sef on 2008-05-30
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by Kuniva on 2008-05-30
> **bigken said:**
> yes use any cd

it might not have a passwordPicked up friend's recovery disk. Worked like charm. Something made me think I would need password.

Windows setup saw partition, noticed its corrupted, scanned the structure, determined its NTFS and repaired with one single command: fixboot!

Can't remember when was last time that Microsoft product worked so flawlessly.

Thanks for help!

> **Sef said:**
> Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

Appreciate the response even thought it didn't help me. Thanks.

---

