---
title: "grub-install error"
date: 2005-11-27
forum: General Help
---

### Post by colapso on 2005-11-27
Hi!
I installed Ubuntu a few days ago, and now I've installed Windows. After this, I want to recover grub. I've followed a how to in this forum, but when I try to install grub (grub-install /dev/hda) I have a message: "can't read stage1"
Anybody knows what is the problem?

Thank you!

---

### Post by Randy Sparks on 2005-11-27
Are you running it with sudo? ie

sudo grub-install /dev/hda

---

### Post by colapso on 2005-11-27
yes, I run it with sudo... but it doesn't work

---

### Post by Xian on 2005-11-27
Sounds like you need to reinstall grub to the MBR.
Read this: [How-To Restore Grub](http://www.ubuntuforums.org/showthread.php?t=24113).

---

### Post by colapso on 2005-11-27
Thank you!
Now I have my grub working again (and my Breezy also :) In fact, after putting grub in MBR, I've changed my menu.lst because the Ubuntu installer wrote something wrong, but that's all! It works!!

Thanks again.

---

