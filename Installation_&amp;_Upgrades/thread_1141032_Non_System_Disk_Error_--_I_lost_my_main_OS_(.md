---
title: "Non System Disk Error -- I lost my main OS :("
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by FredJones on 2009-04-28
I have a machine which had Windows 2000 in the first partition and then it had later on Ubuntu 8 and OpenSUSE. I just now installed Ubuntu 9 over the OpenSUSE. The grub comes up and I see Ubuntu 9, Win2K and Ubuntu 8. 

Ubuntu 9 of course works fine, but when I select Win2K, I get:

Starting up...

Non-system disk
Press any key to reboot

and that's it. Of course all the files are there in the first partition as I didn't touch it. Anyone know how to fix this? I could try Win2K repair but won't that ruin my grub also?

Funny thing is that this is the 10th OS I have installed on this machine since I put Win 2K on and this is the first time I ever had a problem. :(

---

### Post by FredJones on 2009-04-28
I tried now to boot into Ubuntu 8 and it says sbd8 partition not found. But in Ubuntu 9 I see:

```

$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5dd8dcb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204819+  ee  GPT
/dev/sda2              26       13101   105025372   af  Unknown
/dev/sda3           13117       24322    89999700    b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008b5f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sdb2            3188        3697     4096575    7  HPFS/NTFS
/dev/sdb3            3698       10071    51199155    7  HPFS/NTFS
/dev/sdb4           10072       31010   168192517+   5  Extended
/dev/sdb5           10072       11287     9767488+  83  Linux
/dev/sdb6           11288       11409      979933+  82  Linux swap / Solaris
/dev/sdb7           11410       23567    97659103+  83  Linux
/dev/sdb8           23568       24904    10739421   83  Linux
/dev/sdb9           24905       31010    49046413+  83  Linux

```

Oh, now I see this message

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

```

I think maybe that's the issue. I don't know what it means nor how to fix it, however. FYI I did install OSX86 on this machine, but on a separate hard drive. It did somehow mess with the main drive, however, that's true. I recall that now--I had to do the Windows/DOS check disk thing after I installed OSX.

What do I do now?

---

