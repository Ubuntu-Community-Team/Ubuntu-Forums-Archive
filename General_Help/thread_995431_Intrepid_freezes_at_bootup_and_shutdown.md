---
title: "Intrepid freezes at bootup and shutdown"
date: 2008-11-27
forum: General Help
---

### Post by le_vainqueur on 2008-11-27
Whenever I boot up Intrepid on my laptop, it freezes unless I push down a the super key.  I found the same problem here
> [http://ubuntuforums.org/showthread.php?t=924433](http://ubuntuforums.org/showthread.php?t=924433)

Is there a known fix for this?  The user was suggested to try a different kernel in the post above, but no results were reported.  I do not have a different kernel on this machine since it is a fresh install.  I have updated all of my software, so I know that that is not the problem.

---

### Post by le_vainqueur on 2008-11-28
Update:

The bootup/shutdown resumes when I press any key, not just the super key.  Not sure if this info helps, but I thought I should add it.

---

### Post by cariboo on 2008-11-28
Have you done all the updates? this problem was common earlier in the the alpa's of Intrepid. Here is a link to the bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247)

There are several work arounds that you can try.

Jim

---

### Post by le_vainqueur on 2008-11-28
Thanks for the link.  I have done all of the updates.  In the link it says to add "nolapic" to the GRUB kernel options.  I have two questions.

1. How is this done?
2. Are there any other effects that doing this will have on my system?

Thanks

---

### Post by le_vainqueur on 2008-11-29
*bump*

---

