---
title: "Odd GRUB issue..."
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by ArchCorsair on 2008-12-03
Before I state my issue I would like to say I'm using opensuse not ubuntu. But I am using ubuntu live cd to try to fix my issue.
**The Issue**
Installed opensuse 11 on the 2nd harddrive of my laptop. Installation went well, booted into it, ran all updates, was prompted to reboot due to kernel update. I reboot - BAM I'm hit with a GRUB Error 17

After that, i boot into handy ole' Ubuntu 8.04 livecd and do:
```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd1,0)
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd1,0)
setup (hd1,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,0) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.

```
setup succeeds, everything is okay, I reboot and still GRUB error 17

any ideas?

edit: here's my fdisk -lu output
```
root@ubuntu:~# fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e045244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   295081919   147540928+   7  HPFS/NTFS
/dev/sda2       295081920   312576704     8747392+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x053e5bef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   304094384   152047161   83  Linux
/dev/sdb2       304094385   312576704     4241160   82  Linux swap / Solaris
```

---

### Post by caljohnsmith on 2008-12-03
If you can set your BIOS to boot your OpenSUSE sdb drive on start up, then just do:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
In other words, "setup (hd1)" installs Grub to the MBR (Master Boot Record) of the drive so you can boot it, whereas "setup (hd1,0)" installs Grub to the boot sector of the OpenSUSE sdb1 partition; the latter case is useful when you want to "chainload" booting OpenSUSE from another distro. If for some reason you can't change your BIOS to boot the sdb drive on start up, you can use "setup (hd0)" above to install Grub to the MBR of sda. That's less ideal though since then your drives will be dependent on each other for booting, which means more risk for problems. How about trying the above commands and let me know how it goes. :)

---

### Post by ArchCorsair on 2008-12-03
> **caljohnsmith said:**
> If you can set your BIOS to boot your OpenSUSE sdb drive on start up, then just do:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
In other words, "setup (hd1)" installs Grub to the MBR (Master Boot Record) of the drive so you can boot it, whereas "setup (hd1,0)" installs Grub to the boot sector of the OpenSUSE sdb1 partition; the latter case is useful when you want to "chainload" booting OpenSUSE from another distro. If for some reason you can't change your BIOS to boot the sdb drive on start up, you can use "setup (hd0)" above to install Grub to the MBR of sda. That's less ideal though since then your drives will be dependent on each other for booting, which means more risk for problems. How about trying the above commands and let me know how it goes. :)

Thanks, I'm going to try this and report back with the results.

---

### Post by Foxgguy2001 on 2009-01-18
This worked perfect for me!  Thanks!

---

