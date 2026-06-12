---
title: "Difficulty reinstalling grub from live cd"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by JanisL on 2009-09-23
Hello, I am having difficulties reinstalling grub after installing windoze xP. I am trying to dual boot on my laptop and I installed ubuntu first then windows second.

I am currently trying to reinstall grub from the live CD but with little success so far.

Here is the output from fdisk -l
```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc51bc51b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5559    44652636    7  HPFS/NTFS
/dev/sda2            5560        6083     4209030    5  Extended
/dev/sda3            6084       14593    68356575   83  Linux
/dev/sda5            5561        6083     4200997+  82  Linux swap / Solaris

```

Now I want to be able to boot to sda3 but I'm not entirely sure what to do as entering in:
sudo cat /boot/grub/menu.lst
gets
cat: /boot/grub/menu.lst: No such file or directory

Any help would be greatly appreciated!

---

### Post by Elfy on 2009-09-23
Have you done this?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring GRUB](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Restoring GRUB)

If so where do you get the errors?

---

### Post by JanisL on 2009-09-23
Problem solved, thanks!

---

