---
title: "How to enable user privilege to &quot;Use tape drives&quot;?"
date: 2008-08-04
forum: General Help
---

### Post by jhsachs on 2008-08-04
I'm a new user of Ubuntu (v8.04).  I'm trying to familiarize myself with it by accomplishing several tasks which are necessary preparation for using the system to do work.

One of these tasks is learning how to back up the system.  I back up my computer on tape, so to run backups I need to be able to use my tape drive.

Unbuntu knows the tape drive is there. There's a file in /dev/tape/by-id which describes it precisely. (It's an IBM Ultrium I drive with a SCSI interface, BTW.) But when I look at my user privileges in “Users and Groups,” the “Use tape drives” item is cleared, and is disabled so that I can't put a tick on it.

I thought I could fix this by opening “Users and Groups” through sudo, but when I did that I found exactly the same thing: “Use tape drives” disabled, can't be ticked.

What's the trick to add the tick?

---

### Post by jhsachs on 2008-08-15
I found the answer to this elsewhere, so I'm posting it for the benefit of anyone who comes after.

First, I discovered that I do not actually need permission to "Use tape drives" to use the tape drive.  I tried it with the dump utility, and it worked fine.  What "Use tape drives" is for remains a mystery.

Second, there is an "Unlock" button in the Use Permissions window which does just what its name says: unlock the permissions so that (in gksudo) one can tick and untick the options.

---

