---
title: "GRUB problem..."
date: 2008-11-12
forum: General Help
---

### Post by JamesD426 on 2008-11-12
I just turned on my laptop with 8.04 and XP and it froze right after I logged in. I rebooted and it did the same thing. When I tried again, it came up with an error message right after I selected Ubuntu. It says

find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.1st

Error 15: File not found

Press any key to continue 

Then it takes me to a list to find other files (which only lead to another Error 15), go to command line, reboot or halt. 


Last time I booted Ubuntu, everything was fine. I was on XP last, and I didn't change anything on the HD. The last thing I  was messing with were the Display settings while I was trying to get a second monitor to work. 

Any suggestions? 

Thanks,

-James

---

### Post by click4851 on 2008-11-12
whenever I have Grub problems, I always try the SuperGRUB disk first and go from there....?

---

### Post by caljohnsmith on 2008-11-12
Since you have a Wubi installation of Ubuntu, unfortunately the Super Grub Disk is not going to help you. If you have your Windows XP Install CD, I would boot that, go into the "recovery console", and run:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. See if that works first to get Ubuntu booting again.

---

### Post by Sef on 2008-11-12
Moved to wubi forums.

---

