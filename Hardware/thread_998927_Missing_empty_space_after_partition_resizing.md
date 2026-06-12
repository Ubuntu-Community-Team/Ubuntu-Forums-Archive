---
title: "Missing empty space after partition resizing"
date: 2008-12-01
forum: Hardware
---

### Post by kartal on 2008-12-01
Hi

I have resized my ubuntu partition by using PartedMagic live cd. Everything works fine. However I do not see the new empty space. Before my ubuntu drive way 17gb. I scaled it up to 29gb(shrinking another fat32 partition). When I check the drive and space size in Gparted under Ubuntu. I am not seeing the new empty space. Drive says total 29.5 gb and has only 2.2 gb free.

How can I release the empty space?

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26        3253    25924902+  af  Unknown
/dev/sda3   *       15601       19457    30981352+  83  Linux



thanks

---

### Post by butsh on 2008-12-05
i have the same problem

---

### Post by kartal on 2008-12-05
I use Macbook pro and refit boot manager. I have found that you need to use refit to write new partition table(after resizing). If you are not using mac computer you might need to find a tool that will let you sync new partition size. If you find it please let me know as well since I might need to install ubuntu on non mac computers as well.

---

