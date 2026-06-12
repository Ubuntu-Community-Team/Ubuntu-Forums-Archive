---
title: "Failed upgrade broke my grub"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by dfoguelman on 2009-06-21
Hi guys, I was upgrading a lapton vía wifi and connection was failing. During the update some (sorry hadn't saved error descriptions) errors windows apeared. I kept escaping those windows and after reboot no grub option would work.

Now after selecting a grub option this error prompts:
> Error 15: File not found


Tryed to make a backup using Live CD but it was useless due to the protection layer...

Any thoughts? I would like to provide logs, where could I find the neaded ones?

Thanks in advanced,

D

---

### Post by jimv on 2009-06-22
If you're on the Live CD, post these two things.  The output of "sudo blkid", and the contents of /boot/grub/menu.lst (from the hard drive, not the Live CD).

---

