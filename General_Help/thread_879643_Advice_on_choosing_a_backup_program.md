---
title: "Advice on choosing a backup program?"
date: 2008-08-04
forum: General Help
---

### Post by jhsachs on 2008-08-04
Last night I [[COLOR="Blue"]posted a question[/COLOR]]("http://ubuntuforums.org/showthread.php?t=879407") about how to give myself the "Use tape drives" permission so that I can run backups.  This is a related request: I'm seeking advice on choosing a backup program.

I looked at the results of a search for "backup" in Software Sources, and found the following packages that look like they might be appropriate:

afbackup
Amanda
flexbackup
Mondo

At this point I'm not prepared to make an intelligent choice without installing all four packages and trying them.  I don't have enough context even to interpret the short descriptions I found.  For example, the description for afbackup says it's appropriate for users with simple needs, for whom Amanda might be overkill.  That could be me, but I don't have any sense of how complex Amanda is, or how simple afbackup is.

I have a single desktop system with a tape drive, on which I plan to make periodic disaster recovery backups, and separate periodic full backups of data supplemented by daily differential backups.  (This is the approach that I have used for years with Microsoft Windows.)  For this purpose I can easily handle tape rotation by hand. I can't foresee needing to back up anything more than a home network with two or three machines.  On the other hand, some day a client could ask me to set up or manage a backup system for a commercial operation, and then it would be helpful to have the kind of familiarity with a heavy-duty backup program that comes from regular use.

---

### Post by unoodles on 2008-08-04
Amanda is the only one of those I have tried, and it worked without error. Not too complex, but kindof...

---

### Post by hyper_ch on 2008-08-04
I use my own script with the power of rsync and hardlinks to create incremental snap-shot style backups dating back for 90 days.

---

### Post by Mister.Vash on 2008-08-06
If you are thinking of backing up multiple machines, you might want to take a look at bacula.  It's also in the repos

[http://bacula.org/en/](http://bacula.org/en/)

It's worked for me very well

---

