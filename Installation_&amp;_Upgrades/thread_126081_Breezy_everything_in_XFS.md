---
title: "Breezy: everything in XFS?"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by Stormbringer on 2006-02-05
Hello!

I'm unable to find an answer to my questions in either the forum, the wiki or the official website. I hope you guys can give me a clue ...

Question 1: Is Breezy able to boot, and run, of a native XFS setup (all partitions formatted in XFS)??? As far as I understand grub can boot off an XFS volume, but is this supported by Breezy?

Reason for the question: yesterday my system did a scheduled fsck on the hard drive where I store my data ... and it took about 25 minutes to complete (~280GB on a 400GB drive). That's boring...

Another question related to XFS:
Is it true that a XFS volume isn't able to hold a MBR if the drive is partitioned?  I read about this somewhere ... can't remember where, but its been an article about filesystems.


Question 2: Is there a possibility to convert an ext3 filesystem to xfs without losing data? Google finds a few answers, but they all tell a different story.

Would be thankful if anyone could enlighten me on this matter.

Thanks, Storm.

---

### Post by el3ktro on 2006-02-05
Honestly, I would not recommend you XFS. I had a power failure at my house once, and both my desktop machines failed to boot afterwards. Luckily I always make backups. But besides that, Breezy should handle XFS just fine for everything. If you're in doubt, just try it. I don't know of a way to convert ext3->xfs, so you have to reformat anyway (unless somebody knows a way of how to do this!)

Tom

---

### Post by Stormbringer on 2006-02-05
[QUOTE=el3ktro]Honestly, I would not recommend you XFS. I had a power failure at my house once, and both my desktop machines failed to boot afterwards. [/QUOTE]

Really? Some time ago I also had a power failure while the system was running, but my box booted up well after fsck'ing the (ext3) partitions.

[QUOTE=el3ktro]
But besides that, Breezy should handle XFS just fine for everything. If you're in doubt, just try it. I don't know of a way to convert ext3->xfs, so you have to reformat anyway (unless somebody knows a way of how to do this!)
[/QUOTE]

If no one knows if it's possible to boot and run Breezy off XFS then it seems as I will have to try it for myself and see if it works out.

Thanks, Storm.

---

### Post by john_markh on 2006-09-09
Try this : [http://gentoo-wiki.com/HOWTO_Convert_Filesystems](http://gentoo-wiki.com/HOWTO_Convert_Filesystems)

---

