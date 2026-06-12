---
title: "Dual boot 32bit and 64bit, Clonezilla issue"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by ashughes on 2009-07-21
I have an issue dual booting Ubuntu 9.04 32-bit and 64-bit from the same hard drive (different partitions) after restoring using Clonezilla.

I installed Ubuntu 32-bit and 64-bit on separate partitions and set up grub.  Both were booting fine.

Then I created a disk image using Clonezilla.  When I restore from the disk image, Ubuntu 64-bit fails to boot.  I see the bouncing Ubuntu progress bar then it goes to a screen with a blinking cursor.  It blinks for 2 minutes then gives the error "INFO: task khelper blocked for more than 120 seconds." multiple times.

I can press CTRL+ALT+DEL to reset, but Ubuntu never boots.  Ubuntu 32-bit still boots fine.

Has anyone ever run into this issue or a similar issue?  If so, did you solve it?  If so, how?

Any help would be greatly appreciated.

---

### Post by jerrrys on 2009-07-21
just an idea

instead of making a disk image use the second option.  i don't remember what it was called exactly, something like "copy hard disk to hard disk" or "disk to disk"...

---

### Post by ashughes on 2009-07-21
That sort of defeats the purpose.  I want to store the image on an SSH network share so I can restore from it at a later date.

---

