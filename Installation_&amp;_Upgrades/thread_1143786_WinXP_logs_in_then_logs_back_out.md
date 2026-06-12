---
title: "WinXP logs in then logs back out"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by cybercrypt13 on 2009-04-30
I have just installed Ubuntu onto an unused part of my HD and it seems to be working ok.  But when I try to boot into XP I have 2 issues.  1: There are 2 XP things to boot to and the first one doesn't work, so how do I remove it?

2: When the login prompt comes up for XP and I login, it shows a message that its setting everything up, then it flashes that its logging out and it takes me back to the login prompt.  The password is correct but for some reason it won't let me login.

Does anyone know what might be my problem so that I can get XP running again.

Thanks,

---

### Post by cybercrypt13 on 2009-04-30
Well, this morning when I tried to reboot to XP it now won't boot at all.  What is the procedure to reload XP when you have this dual boot thing setup?  Am I about to have to reload the entire computer?

Thanks,

---

### Post by Mark Phelps on 2009-04-30
> **cybercrypt13 said:**
> Well, this morning when I tried to reboot to XP it now won't boot at all.  What is the procedure to reload XP when you have this dual boot thing setup?  Am I about to have to reload the entire computer?

Thanks,
There is no procedure in Linux to "reload" an MS Windows OS.  If you made an OS backup, you could do a restore using MS Windows utilities -- but I'm guessing you didn't do that or you wouldn't be asking about "reload".

If XP is gone, your only option will be to reinstall it, either from the original CD, or if your machine has a recovery partition, using that.

But, we don't know for sure that it's gone ... yet.

Boot into Ubuntu and do an "fdisk -lu" (that's a lowercase L, not a one) from a terminal and post the results here.  That will tell us if the XP partition is still there.

---

