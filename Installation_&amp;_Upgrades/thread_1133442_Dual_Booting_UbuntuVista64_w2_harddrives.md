---
title: "Dual Booting Ubuntu/Vista64 w/2 harddrives"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by Craige4107 on 2009-04-22
Hi all,

I have been running Ubuntu 8.04/8.10 on my laptops and have recently upgraded to 9.04.  I have no problem dual booting Ubuntu and XP or Vista on a single harddrive.  I am interested in dual booting on my gaming computer, using Ubuntu 9.04 and Vista64 on 2 different harddrives.

My question(s):  Is there any special considerations for dual booting using 2 harddrives?  If so, what are they?  Thank you in advance for helping with this question.

---

### Post by Synthros on 2009-04-23
I've done it both ways, and I've found that there are no big difference between the 2 configurations.  In fact, if you're planning to have one entire drive dedicated to Windows and the other to Ubuntu, it makes things even easier because you don't have to do any special partitioning nof a single drive.

Remember, though, just like with dual booting from a single drive, it will save you a lot of headaches to install Windows first, then Ubuntu.  That way, Windows won't come along and wipe out your boot configuration like it would if you install it last.

---

### Post by Mark Phelps on 2009-04-23
It will also faciliate Vista fixes and patches if you install it to its own drive and Ubuntu to a different drive.  I have my system setup that way so that both drives have their own MBRs and nothing I do to either OS runs the risk of corrupting the other.  This way, when I upgrade Ubuntu, it doesn't mess with the Vista drive at all.

The only hangup is that since I disconnect the Vista drive during Ubuntu installs, I have to manually add back the stanza in the grub menu file afterwards.  But that's only a minor inconvenience.

---

### Post by Craige4107 on 2009-04-23
Thanks for the input.  I had pushed ahead, putting Vista64 on one drive, then 8.10 on the other.  Sure enough, Ubuntu wiped my MBR for some odd reason.  I guess I'll try again.  Anyone else have this problem?  Cheers.

---

### Post by Mark Phelps on 2009-04-24
> **Craige4107 said:**
> Sure enough, Ubuntu wiped my MBR for some odd reason.  I guess I'll try again.  Anyone else have this problem?  Cheers.

The default installation writes GRUB to the MBR, in this case, since Vista was probably the "first" drive in the list, it wrote to that drive.

In future, to prevent that, either install from the alternate CD (which provides options of where to write GRUB), or disconnect the Vista drive when installing/replacing Ubuntu.

If you want to repair your Vista drive, you will need to boot from a Vista DVD and do Startup Repair.

---

