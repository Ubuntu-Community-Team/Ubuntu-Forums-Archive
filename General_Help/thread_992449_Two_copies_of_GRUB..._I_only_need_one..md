---
title: "Two copies of GRUB... I only need one."
date: 2008-11-24
forum: General Help
---

### Post by thereaper243 on 2008-11-24
I've just recently started working with Ubuntu. I have no experience with GRUB configuration. I have a working copy of Ubuntu 8.10 installed to one partition, and a working copy of nUbuntu 8.10 on another partition for Security-Dev. When I installed nUbuntu it automatically installed a copy of GRUB. Now, when my computer starts, the nUbuntu GRUB is the copy that runs. I'd like to delete that copy of GRUB and keep the one that is auto-set to start Ubuntu. If someone could help me, it would be greatly appreciated. Please remember that I am very new. I've never really worked with non-GUI systems before.

Thanks,
thereaper243

---

### Post by adult swim on 2008-11-24
the easiest way to do this is to restore ubuntus 8.10 grub from the live cd
here is a link of how to do that [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
maybe the only confusing thing about this is whenever you run find /boot/grub/stage1 you will get two results.  assuming that you have one hard disk and ubuntu's grub is on the first partition you would use root (hd0,0)  if you have questions post back.

---

