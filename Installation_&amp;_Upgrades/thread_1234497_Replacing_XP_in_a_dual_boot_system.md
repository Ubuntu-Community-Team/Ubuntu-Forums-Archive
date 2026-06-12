---
title: "Replacing XP in a dual boot system"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by ronnodas on 2009-08-07
I am looking to install ubuntu to my home PC. This is going to be my first linux install.

I currently have XP and Vista dual booting on the system, on different partitions of one HDD with XP on the primary partition. I want to replace the XP installation with ubuntu. 

What should be the process of installation and should I need to take any steps after the setup for dual booting to work correctly?

Also, I may upgrade the Vista installation to Windows 7 when it releases. Will I then need to reinstall ubuntu (or parts of it) to make it work?

Thanks in advance for your help.

---

### Post by mikewhatever on 2009-08-08
I'd strongly advise leaving the first partition, because that's where Windows keeps its boot loader. If you delete the first primary partition, all the other Windows installation will likely become unbootable.
You can either shrink an existing partition to make space for Ubuntu, or use another hdd.

---

### Post by ronnodas on 2009-08-08
Is there any way I can back up the boot loader and put it back after installing ubuntu?

Also, is it possible to install ubuntu at all on the first partition with Windows installed on another one?

Otherwise I'll just clean install when Windows 7 is released.

---

### Post by mikewhatever on 2009-08-08
> **ronnodas said:**
> Is there any way I can back up the boot loader and put it back after installing ubuntu?

Also, is it possible to install ubuntu at all on the first partition with Windows installed on another one?

Otherwise I'll just clean install when Windows 7 is released.

I don't know, but even if there was a way, a Windows bootloader can't be on an ext3 partition. Shrinking the first partition as much as possible is fine, you can even delete XP, but I wouldn't advise deleting the partition.
As said, Windows always puts its boot loader on the first primary partition, even if the OS itself is installed elsewhere. If you delete that partition and install Ubuntu, Windows will be missing the bootloader files. If you try to reinstall the bootloader, it will automatically attempt to put it on the first primary partition, and will complain about it not being writable or about unknown file system.

---

### Post by ronnodas on 2009-08-08
Ok.

Thanks for your help.

---

