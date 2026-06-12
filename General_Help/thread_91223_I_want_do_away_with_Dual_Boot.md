---
title: "I want do away with Dual Boot"
date: 2005-11-16
forum: General Help
---

### Post by BabaFree on 2005-11-16
I want to reformat my hard drive and do away with my Window XP partition.  What would I need to do in order to keep all my files plus my settings and things like the emails I have in evolution.  Any help would be appreciated.  I've got an 80 gig hard drive and it's partitioned half and half.  
Thanks,
Brandon

---

### Post by Casey on 2005-11-16
[QUOTE=BabaFree]I want to reformat my hard drive and do away with my Window XP partition.  What would I need to do in order to keep all my files plus my settings and things like the emails I have in evolution.  Any help would be appreciated.  I've got an 80 gig hard drive and it's partitioned half and half.  
Thanks,
Brandon[/QUOTE]

Is there any particular reason that you want to reformat the entire drive?  Would you be happy just removing the windows partition (and then if you so desired you could use that space for a linux partition)?

---

### Post by BabaFree on 2005-11-16
How would I use that partition with my existing ubuntu partition?  Would I have to install a new distribution?

---

### Post by bonzodog on 2005-11-16
The other thing you could consider is backing up all your data to be kept to a cd, erase, do a re-install, then on re-install, create a seperate /home partition. Once you have your data on this, you should never need to erase/format it again, as you can then install any other distro/upgrade into the / partition.

---

### Post by BabaFree on 2005-11-16
would backing up my /home directory be enough to keep my email files in Evolution (I'm not sure where they are kept).  After reinstallation, how would I get all the files back into /home?  Copy and paste?
Thanks,
Brandon

---

### Post by afonic on 2005-11-16
[QUOTE=BabaFree]How would I use that partition with my existing ubuntu partition?  Would I have to install a new distribution?[/QUOTE]

You can just make a new partition with that space and mount it somewhere or just resize your /home partition to include this space. No data will be lost, but to be on the safe side, keep backups.

Use the search function, there are other threads about how to do that.

---

