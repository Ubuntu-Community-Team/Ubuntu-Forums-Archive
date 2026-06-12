---
title: "Removing Vista - Question about booting afterwards"
date: 2008-08-08
forum: General Help
---

### Post by dai_vernon on 2008-08-08
I want to reformat my two NTFS partitions that Vista is installed on into ext3 so I can use them.  However, as you can see in this screenshot of my GParted, one of the NTFS partitions is labelled 'boot'.  I believe that this means that if I format this partition I won't be able to boot.  Is this true?  How do I set to boot off my ext3 partition?

---

### Post by mb_webguy on 2008-08-08
The "boot" flag simply means that's a bootable partition, which doesn't really matter as far as GRUB is concerned.  You should be able to reformat that partition without causing any problems.  Afterward, you should be able to boot normally into Ubuntu with the GRUB menu, although you may still see an entry for Windows.  Typing "sudo update-grub" should clear that entry.  If it doesn't, typing "sudo gedit /boot/grub/menu.lst" will allow you to manually edit the GRUB menu and remove the Windows entry.

---

