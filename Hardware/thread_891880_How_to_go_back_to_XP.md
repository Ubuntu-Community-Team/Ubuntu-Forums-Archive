---
title: "How to go back to XP?"
date: 2008-08-16
forum: Hardware
---

### Post by cowsled on 2008-08-16
Heya

I'm currently trying to get my laptop back to XP. It doesn't have an optical drive so, I'm trying to restore it via a Ghost image. Even after restoring the image, Grub still tries to load (fails). I formatted the harddrive and still get the same problem. Can anyone help?

---

### Post by phidia on 2008-08-16
You need to restore the MBR but since you don't have an optical drive I'm not sure what you can do-do you have a floppy drive? 
I believe the dos command is fixmbr see [this]("http://www.computerhope.com/fixmbr.htm").

---

### Post by cowsled on 2008-08-16
Thanks for the reply :)
Is there any way to do it from windows? I can take out the drive and hook it up to a portable.

---

### Post by phidia on 2008-08-16
> **cowsled said:**
> Thanks for the reply :)
Is there any way to do it from windows? I can take out the drive and hook it up to a portable.

Take a look at the guide [here]("http://commandwindows.com/recovery-console-commands.htm"). I think that will do it for you.

---

### Post by cowsled on 2008-08-16
Would clearing the MBR make me lose all my files?

---

### Post by phidia on 2008-08-16
No and usually the fixmbr command just restores the back up or previous MBR.
"fixmbr" doesn't do anything to your partitions. Normally I would reccommend you obtain super grub disk but since you don't have an optical drive that's not much of an option.

---

