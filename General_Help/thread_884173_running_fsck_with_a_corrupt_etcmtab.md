---
title: "running fsck with a corrupt /etc/mtab"
date: 2008-08-08
forum: General Help
---

### Post by mikejt2001 on 2008-08-08
I have a problem with my root filesystem. If I:

	ls -l mtab
I get:
	ls: /etc/mtab: Input/output error


If I ls -l /etc, I see the following line:

?---------   ? ?    ?            ?            ? mtab

A few other files on my root filesystem also show a similar problem. Obviously, my root filesystem is corrupt and needs to be fsck'ed.

It I try to mount it read-only so that I can safely fsck it, I get:

mount -o ro,remount /dev/hda1
mount: can't open /etc/mtab for writing: Input/output error

The problem is that I am on vacation for 3 weeks and only have ssh access. I don't want to risk rebooting it incase it doesn't come back up again. 

This type of problem has to happen at the only time when I'm away from my computers. 

Can anyone suggest an alternative approach, please?

---

