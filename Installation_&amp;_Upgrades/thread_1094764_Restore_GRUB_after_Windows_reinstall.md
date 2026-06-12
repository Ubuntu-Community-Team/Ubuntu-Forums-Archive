---
title: "Restore GRUB after Windows reinstall?"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by kahlil88 on 2009-03-12
My friend is dual-booting Windows XP and Ubuntu 8.10 - the Windows system has been dogged down by viruses and really needs to be re-installed. I realize that doing this would erase GRUB. Can I somehow backup GRUB (I guess it's stored in the MBR?) and restore it after re-installing Windows?

---

### Post by circa82 on 2009-03-12
You might find this helpful [installing GRUB from live CD](http://ubuntuforums.org/showthread.php?t=224351)

Technically, GRUB is already 'backed up' in the /boot/grub folder. When you 'reinstall' it, you're installing the stage1 and 1_5 files from that directory. No need to back it up beforehand.

---

### Post by kahlil88 on 2009-04-16
> **circa82 said:**
> You might find this helpful [installing GRUB from live CD](http://ubuntuforums.org/showthread.php?t=224351)

Technically, GRUB is already 'backed up' in the /boot/grub folder. When you 'reinstall' it, you're installing the stage1 and 1_5 files from that directory. No need to back it up beforehand.
Yay! Thanks, that was very helpful. I guess this officially disproves the myth that Windows must be installed first.

---

