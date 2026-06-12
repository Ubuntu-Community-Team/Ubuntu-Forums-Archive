---
title: "ACPI question and the new Grub2"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by itsmoonsoo on 2009-11-11
I just installed a fresh copy of Ubuntu 9.10 on a new Toshiba I bought solely to put linux on.  Unfortunately, this computer's BIOS is incompatible with Ubuntu or something so I had to turn off acpi to install the OS.  

In addition, I need to turn off acpi in the boot kernel like this gentleman did who has the exact same problem as me ([http://ubuntuforums.org/showthread.php?t=1301101](http://ubuntuforums.org/showthread.php?t=1301101)).  The problem is that I made a fresh install rather than an upgrade so menu.lst doesn't exist.  How can I edit the boot kernel to get acpi off in grub2?

Thanks!

What would really be great is if anyone could give me a fix to make ACPI compatible with my notebook in the first place!

---

### Post by gawhelan on 2009-11-16
I just had to do this myself. The file you need to edit is > /etc/default/grub
Look for the line:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
and change it to:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
Then you need to update the config files by running:
```
sudo update-grub
```

Check out the [Grub2 community docs]("https://help.ubuntu.com/community/Grub2") for more info.

---

