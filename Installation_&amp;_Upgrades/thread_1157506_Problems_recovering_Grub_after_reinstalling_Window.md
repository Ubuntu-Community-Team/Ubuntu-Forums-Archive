---
title: "Problems recovering Grub after reinstalling Windows XP"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by Mike Hollinshead on 2009-05-12
I run Ubuntu and Windows XP Professional on the same drive.

I did a clean reinstall of Windows (reformatted the partition from the Ubuntu CD).

Of course, I lost the Grub, so I went to recover it using the CD to enter the root.

The usual commands worked until I did setup (hd0), as under:

grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

grub> 

How do I get around this?

Thanks,

Mike Hollinshead

---

