---
title: "Problem with connecting portable hard drive"
date: 2009-02-18
forum: Hardware
---

### Post by LT.Was on 2009-02-18
Hello all!

My portable hard drive stopped working on my XP system, but it has alot of files still on it. A colleague of mine recommended I use Ubuntu to try to "fish" the files out of the drive. When I started Ubuntu, it recognized my portable hard drive but when I tried to access it further, I received an error saying Unable to Mount. I have heard that you are able to "force mount" a drive through Linux. I'm still relatively new to Ubuntu so I was wondering if anyone could help me with this.

---

### Post by taurus on 2009-02-18
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by LT.Was on 2009-02-18
As I am on a separate computer using this forum, I'll just type what it says for my portable hard drive.

Disk /dev/sdc: 320.0 GB, 220072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units= cylinders of 16065 * 512 - 8225280 bytes
Disk identifier: 0xe22bcc8a
Device Boot       Start     End           Blocks             Id           System
/dev/sdc1   *        1     38913         312568641             7          HPFS/NTFS

---

### Post by taurus on 2009-02-18
What happens when you try to mount it from a terminal with

```
sudo mkdir /media/sdc1
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
df -h
```
If you need to force mount it, you could run

```
sudo mkdir /media/sdc1
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1 -o force
df -h
```

---

### Post by LT.Was on 2009-02-18
does the "df -h" go directly after "force" in the second command?

---

