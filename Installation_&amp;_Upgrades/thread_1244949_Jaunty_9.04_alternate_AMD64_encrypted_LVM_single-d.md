---
title: "Jaunty 9.04 alternate AMD64 encrypted LVM single-disk install fails in grub-install"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by Blueshell on 2009-08-20
I'm trying to install from the Jaunty/9.04 alternate AMD64 CD on a single 1.5TB disk, using LVM and encrypting the entire thing, using the guided installation, on a machine with no other disks and 4GB RAM.  The disk had previously been zeroed and then had a single whole-disk JFS created on it as part of testing the disk.  (I can't recall if I created JFS on the raw device, or created a single partition and then created the JFS in that, but it shouldn't matter, since I told the installer to just wipe the entire disk.)  When the installer is close to finishing, it gives "Executing 'grub-install (hd0)' failed."  Retrying just the installation of grub fails identically.  Continuing gives me an apparently-okay install but no bootloader.  I booted the same CD in rescue mode, gave my passphrase, mounted the filesystem, and then tried '/usr/sbin/grub-install "(hd0)"', which gave me a couple of lines of text followed by "grub-probe: error: no mapping exists for foo-root" (foo was the name of the machine) and then clearly some error in the script, namely "[; 494: =: unexpected operator", followed by "The file /boot/grub/stage1 not read correctly."

Searching hasn't revealed much of use except this thread:  [http://ubuntuforums.org/showthread.php?t=1135662](http://ubuntuforums.org/showthread.php?t=1135662), which talks about booting the LiveCD and installing grub from there---but does this mean I can't install encrypted-LVM on AMD64?

My next move might be try the manual-install option, or to try to install an unencrypted /boot and then manually create an encrypted LVM by hand, but I was hoping to at least see what the automatic install would give me before spending a whole lot of time going in that direction.

Thanks!

---

