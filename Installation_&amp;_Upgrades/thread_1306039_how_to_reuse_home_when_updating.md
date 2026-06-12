---
title: "how to reuse /home when updating?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by ricpat51 on 2009-10-30
hi everyone,
I'm updating from 9.04 to 9.10 and a doubt just came out...
...this is my partition table.

```

/dev/sda1              63    29302559    14651248+  83  Linux
/dev/sda2        29302560   519268994   244983217+  83  Linux
/dev/sda3   *   519268995   621040769    50885887+   7  HPFS ou NTFS
/dev/sda4       621040770   625137344     2048287+  82  Linux swap / Solaris

```

this partition on sda2 is my /home and I wanted to reuse it then I'd not lose my personal files. Is there a way for that? I tried to install but the partitioner mark it to format in the installation.
Sorry for my Englisn.
Thanks in advance

---

### Post by Roasted on 2009-10-30
When you install Ubuntu, select manual partitioning mode (advanced).

Mount your usual root partition as root ( / ), and select format. Also select the file system type.

For home, do the same thing, BUT DO NOT SELECT FORMAT. Mount the file system type, EXT3, EXT4, whatever, and select the mount point as /home. But do not check that magic box to format it.

---

