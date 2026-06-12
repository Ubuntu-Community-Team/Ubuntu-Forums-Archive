---
title: "[SOLVED] Grub4dos help"
date: 2008-11-16
forum: General Help
---

### Post by dakkar9999 on 2008-11-16
Hi,  let me firt take my story from the beginning, it might contain some clue!

Ok, I had a nicely running Ubuntu 8.04 wubi install, but it ran out of space.  I decided to give it it's own hd intall.  I took a second drive (80gig)  at first I did a regular install from the live cd and had a linux partition installed.  Unfortunately, I had frequent lockup requiring hard reboot.  I think that hd has some physical damage.  In windows, it only shows as a 30 gig hd.  So I was thinking that perhaps, windows was able to limit the use of the hd to the part that was still ok.  That hd was still working flawlessly in windows (as a 30gig)

So, I removed my old wubi install and tried to reinstall it but using that 30gig hd as target (linux was trying to use the whole 80 if doing install from live cd's, but it seemed to lock up randomly, tried with various flavor of linux...)

Now, to my current problem, when I chose ubuntu as the os to start, I get to the grub>  prompt.

From reading the forum, I have tried various fix, ex. running chkdsk /r to repair the boot.

From the grub> prompt, I'm able to see the install using kernel+tab(/ubuntu/disks+tab).  But what do I do with this info?

Also, I have seen that the menu.lst might be need some change, but where do I find it in a wubi install?  I've looked at the content of 2 different menu file located in the wubi folders, but they look nothing like they should ( i now have some experience in changing menu.lst from my other install experiments)

Sorry for the long story, but here are the facts.

Thanks in advance for the help!

---

### Post by dakkar9999 on 2008-11-16
Solved.  Actually the hd does not want to cooperate.  Tried to install to a different hd and it worked fine.

---

