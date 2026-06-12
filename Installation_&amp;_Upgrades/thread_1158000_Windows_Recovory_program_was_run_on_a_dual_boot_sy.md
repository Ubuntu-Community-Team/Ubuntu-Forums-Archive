---
title: "Windows Recovory program was run on a dual boot system Is the linux partion gone?"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by obiyoda on 2009-05-13
So I set ubuntu up for a friend of mine. He wanted the option to be able to dual boot into vista. Not a problem however somebody else started using the computer and went into the vista recovery partition from the grub boot menu. Now the computer is booting into windows... Well trying to they didn't complete the install process. So my question is is the linux partition gone? If so is there any way to recover it. I've told them not to turn on the computer until I can get to look at it which will be later this weekend. Normally I would just ssh in but the box is well unusable right now.

---

### Post by Partyboi2 on 2009-05-13
Hi, if you can boot a ubuntu live cd and open a terminal and type
```
sudo fdisk -lu
``` this should show you if the ubuntu partitions are still there.
If they reinstalled Vista you will need to restore grub which can be done from a ubuntu live cd following [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")

---

